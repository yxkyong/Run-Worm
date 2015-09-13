# Run-Worm
用C语言的控制台编写的一个叫Run Worm的小游戏。
#include <iostream>
#include <conio.h>
#include <stdio.h>
#include <windows.h>
#include <stdlib.h>
#include <string.h>
#include <time.h>

char window[20][30];
int count=0;
void setup();
void putout();
void move();
void enter();
void putout2();
int main(void)
{
   int c;   
 enter();
	setup();
	move();
    c=getch();   
	    c=getch();  
    while(c!='q')
	{
	     setup();
		
       move();
	   c=getch();
	    c=getch();
	  }
	 
	return 0;
}
void enter()
{
    int i,j,c,step=1;
	//界面
	window[8][10]='G';
	window[8][11]='a';
	window[8][12]='m';
	window[8][13]='e';
	window[9][6]='R';
	window[9][7]='u';
	window[9][8]='n';
	window[9][9]=' ';
	window[9][10]='a';
	window[9][11]='n';
	window[9][12]='d';
	window[9][13]=' ';
	window[9][14]='T';
	window[9][15]='u';
	window[9][16]='r';
	window[9][17]='n';
	window[11][9]=16;
	window[11][10]='S';
	window[11][11]='t';
	window[11][12]='a';
	window[11][13]='r';
	window[11][14]='t';
    window[13][10]='H';
	window[13][11]='e';
	window[13][12]='l';
	window[13][13]='p';
	window[16][10]='P';
	window[16][11]='r';
	window[16][12]='e';
	window[16][13]='s';
	window[16][14]='s';
	window[16][15]=' ';
	window[16][16]='d';




	putout();
	while(c=getch())
	{
	    switch(c)
		{
		case'w': case's':
			 {
			   if(step==1)
			   {
			      window[11][9]=' ';
				  window[13][9]=16;
			      step=2;
				  system("cls");
				  putout();
				  break;
			   }
			   
			 
                if(step==2)
				{
				window[13][9]=' ';
					window[11][9]=16;
					step=1;
					 system("cls");
				  putout();
				  }
				break;
			}
		case'd':
			{
				if(step==1)
			goto finish;
				if(step==2)
				{
				  system("cls");
					printf("\n\t\t游戏规则\n");
				  printf("  在Run and turn的游戏中你将会是一只被诅咒的小虫子\n");
				  printf("  邪恶的诅咒使你必须不断前进(速度是不稳定的！)\n  通过不断吸收爱心来维持生命\n");
				  printf("  但拐弯需要消耗大量能量,在没吃到爱心时,仅有三次拐弯的体力\n");
				  printf("  吃到爱心后重新获得三次拐弯的体力,注意哦\n ");
				  printf("  别错过拐弯的机会哦！比比看谁爱心吃的多!\n");
				  printf("  拐弯由'w','a','s','d'控制,按两下w退出介绍");

					 getch();
				  break;
				
				
				}
			}
		}
	
	
	
	
	}

finish:;



}


void setup()
{
   int i,j;
   
   for(i=0;i<20;i++)
	   for(j=0;j<30;j++)
	   {
	       window[i][j]=' '; 
	   }

		putout();
}
void putout()
{
int i,j;
	for(i=0;i<20;i++)
	   for(j=0;j<30;j++)
	   {
	   if(j==29)
	   {
	   printf("%c",window[i][j]);
	   printf("\n");
	   }
	else
    printf("%c",window[i][j]);
	   }
}
void move()
{
    int m=18,n=10,x,y,step=0,num=0;
	int c,compare;
	FILE *fp1,*fp2;
    srand((int)time(NULL));
	window[m][n]=15;

	system("cls");
	putout();
	x=rand()%19+1;
	y=rand()%28+1;
	window[x][y]=3;
while(c=getch())
{    
    
		switch(c)
	   {
		
	   case 'w' :
		   {
	num=num+1;
       while(!kbhit())
	   {
          window[m][n]=' ';
		   m=m-1;
           window[m][n]=15;
           system("cls");
		   putout();
		   		if(m==x&&n==y)
	{
	  window[m][n]=15;
	 system("cls");
	 step=1;
	  putout();
	  num=0;
	  count=count+1;
		}
		if(step==1)
		{
		step=0;
		x=rand()%19+1;
  	  y=rand()%28+1;
	  window[x][y]=3;
	  system("cls");
	  putout();
		}

}
	   if(num==3)
		   goto finish;
		 break;
		   }
	   case 'd':
		{
			num=num+1;
	      while(!kbhit())
{
           window[m][n]=' ';
		   n=n+1;
           window[m][n]=15;
           system("cls");
		   putout();
		   		if(m==x&&n==y)
	{
	  window[m][n]=15;
	 system("cls");
	 step=1;
	  putout();
	  num=0;
	   count=count+1;
		}
		if(step==1)
		{
		step=0;
		x=rand()%19+1;
  	  y=rand()%28+1;
	  window[x][y]=3;
	  system("cls");
	  putout();
		}

}
		  if(num==3)
		   goto finish;
		      break;
		}
	   case 's':
		   {
			   num=num+1;
	      while(!kbhit())
{
           window[m][n]=' ';
		   m=m+1;
           window[m][n]=15;
           system("cls");
		   putout();
		   		if(m==x&&n==y)
	{
	  window[m][n]=15;
	 system("cls");
	 step=1;
	  putout();
	  num=0;
	   count=count+1;
		}
		if(step==1)
		{
		step=0;
		x=rand()%19+1;
  	  y=rand()%28+1;
	  window[x][y]=3;
	  system("cls");
	  putout();
		}

}
		  if(num==3)
		   goto finish;
		      break;
		   }
	   case 'a' :
		   {
			   num=num+1;
while(!kbhit())
{
           window[m][n]=' ';
		    n=n-1;
           window[m][n]=15;
           system("cls");
		   putout();
		if(m==x&&n==y)
	{
	  window[m][n]=15;
	 system("cls");
	 step=1;
	  putout();
	  num=0;
	   count=count+1;
		}
		if(step==1)
		{
		step=0;
		x=rand()%19+1;
  	  y=rand()%28+1;
	  window[x][y]=3;
	  system("cls");
	  putout();
		}
}
      if(num==3)
		   goto finish;
		      break;
	   }	
	}
}
finish: {
		   window[m][n]=' ';
		   window[x][y]=' ';
		   window[10][5]='Y';
		   window[10][6]='O';
		   window[10][7]='U';
		   window[10][8]='R';
		   window[10][9]=' ';
		   window[10][10]='S';
		   window[10][11]='C';
		   window[10][12]='O';
		   window[10][13]='R';
		   window[10][14]='E';
		   window[10][15]=':';
		   window[10][16]=3;
		   window[10][17]='*';
		   window[10][18]=count;
           window[8][10]='Y';
		   window[8][11]='O';
		   window[8][12]='U';
		   window[8][13]=' ';
		   window[8][14]='L';
		   window[8][15]='O';
		   window[8][16]='S';
		   window[8][17]='E';
		   window[8][18]='!';
		   window[12][3]='P';
		   window[12][4]='r';
		   window[12][5]='e';
		   window[12][6]='s';
		   window[12][7]='s';
		   window[12][8]=' ';
		   window[12][9]='a';
		   window[12][10]='n';
		   window[12][11]='y';
		   window[12][12]=' ';
		   window[12][13]='k';
		   window[12][14]='e';
		   window[12][15]='y';
		   window[12][16]=' ';
		   window[12][17]='t';
		   window[12][18]='o';
		   window[12][19]=' ';
		   window[12][20]='r';
		   window[12][21]='e';
		   window[12][22]='t';
		   window[12][23]='r';
		   window[12][24]='y';
		   window[14][3]='P';
		   window[14][4]='r';
		   window[14][5]='e';
		   window[14][6]='s';
		   window[14][7]='s';
		   window[14][8]=' ';
		   window[14][9]='q';
		   window[14][10]=' ';
		   window[14][11]='t';
		   window[14][12]='o';
		    window[14][13]=' ';
			 window[14][14]='Q';
			  window[14][15]='u';
			   window[14][16]='i';
			    window[14][17]='t';
				fp1=fopen("record.txt","rb");
		
				fscanf(fp1,"%d",&compare);
				if(count>compare)
				{
				     system("cls");
					 printf("\n\n\n\n\n\n\n\tBreak the Record!");
					 Sleep(2000);
					 fclose(fp1);
					 fp2=fopen("record.txt","w+");
					 fprintf(fp2,"%d",count);
					 fclose(fp2);
				
				
				
				}
		  
		}
		system("cls");
		putout2( );
	
}
void putout2()
{
   int i,j;
	for(i=0;i<20;i++)
	   for(j=0;j<30;j++)
	   {
	   if(j==29)
	   {
	   printf("%c",window[i][j]);
	   printf("\n");
	   }
	else if(i==10&&j==18)
		printf("%d",count);
	else
    printf("%c",window[i][j]);
	   }
}

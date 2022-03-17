# -#include <stdio.h>
#include <windows.h>
#include <conio.h>
char printMap[9][12]={"*#*********",
					  "***###*###*",
					  "###**#****#",
					  "*#**###**#*",
					  "***********",
					  "#####*##*##",
					  "*##*****#*E",
					  "***#*###**#",
					  "*#*********"};


void pos(int a,int b)
{
	COORD pos;
	pos.X=b;
	pos.Y=a;	
	SetConsoleCursorPosition(GetStdHandle(STD_OUTPUT_HANDLE),pos);
}

void cycle()
{	
	int x=0,y=0;
	char MOVE;
	while((x==6&&y==10)==0)
	{
		pos(x,y);
		MOVE=getch();
		if(MOVE=='s')
		{
			if(printMap[x+1][y]=='*')
			{
				x++;
			}
		}
		if(MOVE=='w')
		{
			if(printMap[x-1][y]=='*')
			{
				x--;
			}
		}
		if(MOVE=='a')
		{
			if(printMap[x][y-1]=='*')
			{
				y--;
			}
		}
		if(MOVE=='d')
		{
			if(printMap[x][y+1]=='*'||printMap[x][y+1]=='E')
			{
				y++;
			}
		}
	}
	putchar('\n');putchar('\n');putchar('\n');
}


int main()
{
	for(int Q=0;Q<9;Q++)
	{
		printf("%s\n",printMap[Q]);
	}
	cycle();
	printf("恭喜你，完成迷宫\n");
}

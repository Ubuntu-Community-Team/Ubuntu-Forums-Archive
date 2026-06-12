---
title: "Anjuta problem"
date: 2006-09-20
forum: Absolute Beginner Talk
---

### Post by lazyme on 2006-09-20
Hey guys I just installed Anjuta for Ubuntu.But im having problem building a code with sqrt function in it even after including math.h.The code compiles successfully in Anjuta but refuses to build.Also im having no problems in executing the same code from the editor using the -lm switch.So how do I get it to work in Anjuta?Please explain to a noob.

---

### Post by MonkeeOfEvil on 2006-09-20
I have anjuta installed, use the [code ] [/code ] tags ( without the space before the closing ] ) and copy/paste the code your trying to run in between the tags so we can see what your working with.

:)

---

### Post by lazyme on 2006-09-20
Buddy it is a 200 line code and like I said it worked flawlessly in windows and also with gcc -lm switch.How do I include -lm switch in Anjuta?

---

### Post by lazyme on 2006-09-20
Building the file using gcc I had no problems.
> 
lazyme@lazyme-desktop:~$ gcc ant.c -lm
lazyme@lazyme-desktop:~$ ./a.out

Enter the no. of cities : 3

Enter x and y co-ordinates for city 1 : 5 5

Enter x and y co-ordinates for city 2 : 10 5

Enter x and y co-ordinates for city 3 : 12 5

Enter total no. of ants1

Enter start city : 0

Next city=1

Next city=2
 


Here's the code if that would be of any help
```

#include <stdio.h>

#include <stdlib.h>

#include <math.h>

#include "/home/lazyme/RANDOM.C"



#define B 2



struct cord

{

  int x, y;

} Co[30];

struct edge

{

  float distance,pheromone;

}Edge[30][30];



typedef struct ant

 {

  int unvisited[30];

  int path[31];

  float dist;

  }ant;

  ant ant1[10];



int caledge();

float calprobab(ant,int,int);

int visited[30] =

{

  '\0'

};



int caldistance(int);

float caldist(int,int);

int n,ants,next_city;

float shortdist = 0,a,b,dist;

float probability();

int transition(ant *,int);



int main()

{

  int i;

  int start,first;



  printf("\n Enter the no. of cities : ");

  scanf("%d", &n);



  for (i = 0; i < n; i++)

  {

	printf("\nEnter x and y co-ordinates for city %d : ", i + 1);

	scanf("%d%d", &Co[i].x, &Co[i].y);

  }

  caledge();



   printf("Enter total no. of ants");

   scanf("%d",&ants);

   printf("\nEnter start city : ");

   scanf("%d", &start);

   ant1[0].unvisited[start]=1;

   next_city=start;



   for(i=0;i<n-1;i++)

   {

   ant1[0].path[i]=next_city;

   ant1[0].unvisited[next_city]=1;

   next_city=transition(&ant1[0],next_city);

   printf("\nNext city=%d",next_city);



   }

   ant1[0].path[i]=start;

   printf("\npath=");

   for(i=0;i<n+1;i++)

   printf("%d\t",ant1[0].path[i]);



  return 0;

  

}





int caldistance(int start)

{

  int i, j;

  float prevdist = 9999;

  int city;

  for (i = 0; i < n; i++)

  {

	if (visited[i] == 0)

	{

	  a = pow(Co[i].x - Co[start].x, 2);

	  b = pow(Co[i].y - Co[start].y, 2);

	  dist = sqrt(a + b);



	  if (dist < prevdist)

	  {

		prevdist = dist;

		city = i;

	  }

	}

  }

  visited[city] = 1;

  shortdist += prevdist;



  printf("\tCurrent distance : %f", shortdist);



  return city;

}

 int caledge()

 {

   int i,j;

   float a,b,dist;

   for(i=0;i<n;i++)

	{

	 for(j=0;j<n;j++)

	  {

	  if(i!=j)

	   {

		a = pow(Co[i].x - Co[j].x, 2);

		b = pow(Co[i].y - Co[j].y, 2);

		Edge[i][j].distance = Edge[j][i].distance=sqrt(a + b);

		Edge[i][j].pheromone=Edge[j][i].pheromone=1;

		}

	   }

	  }

 return 0;

 }



 float calprobab(ant ant1,int current,int nextcity)

  {

   int i;

   float num,deno=0,probab;



   if((ant1.unvisited[nextcity]==1)||(current==nextcity))

   return 0;



   num= Edge[current][nextcity].pheromone*pow(1/Edge[current][nextcity].distance,B);

	for(i=0;i<n;i++)

   {

	if((!ant1.unvisited[i])&&(i!=current))

	{

	 deno+=Edge[current][i].pheromone*pow(1/caldist(current,i),B);

	 }

	}

	probab=num/deno;





	return probab;

  }



  float caldist(int city1,int city2 )

  {

   a = pow(Co[city1].x - Co[city2].x, 2);

   b = pow(Co[city1].y - Co[city2].y, 2);

   dist=sqrt(a + b);

   return dist;

   }







   int transition(ant *ant2,int current)

	{

	  int next,i;

	  float rnd,q=0.9,max=0,prevmax,maxprob=0,prevprob;



	  rnd=(float)randomMT();

	  if(rnd<=q)

	   {

		 for(i=0;i<n;i++)

		 {

		   if(current!=i&&ant2->unvisited[i]!=1)

		   {

			prevmax= Edge[current][i].pheromone*pow(1/Edge[current][i].distance,B);

			if(prevmax>max)

			{

			 max=prevmax;

			 next=i;

			}

		   }

		 }

	   }

	   else

		{

		 for(i=0;i<n;i++)

		  {

		   if(current!=i&&ant2->unvisited[i]!=1)

		   {

		   prevprob=calprobab(*ant2,current,i);

			if(prevprob>maxprob)

			 {

			  maxprob=prevprob;

			  next=i;

			  }

		   }

		 }

		}

		ant2->unvisited[next]=1;

		return next;

	}

```

The code compiles in Anjuta without errors but on build I get the following errors.

> 
Building file: ant.c ...
gcc       "ant.c"     -o "ant"
/tmp/ccEwQ3s0.o: In function `caldistance':ant.c:(.text+0x521): undefined reference to `sqrt'
/tmp/ccEwQ3s0.o: In function `caledge':ant.c:(.text+0x667): undefined reference to `sqrt'
/tmp/ccEwQ3s0.o: In function `caldist':ant.c:(.text+0x96a): undefined reference to `sqrt'
collect2: ld returned 1 exit status
Completed ... unsuccessful
Total time taken: 0 secs



Please help guys.

---

### Post by lazyme on 2006-09-21
Please can someone help?

---

### Post by climatewarrior on 2007-09-06
I have the same problem and do not know to solve it but at least I know its source. The problem is that Anjuta doesnt know where the libraries are in your computer. You have to tell it where the math.h and all the other libraries you wan to use are. You can tell Anjuta where the libraries are by going to the settings tab in Anjuta clicking in compile and linking settings and in the libraries and include tabs put the paths to the libraries you want to use. In Ubuntu 7.04 the libraries are located in   
usr/include. You can find more info on this link.

[http://www.anjuta.org/anjuta.php?page=documentations&subpage=documents/C/anjuta-advanced-tutorial/index.html](http://www.anjuta.org/anjuta.php?page=documentations&subpage=documents/C/anjuta-advanced-tutorial/index.html)

if you manage to solve it because even though I tried this Im know getting different problems. 

But another fix is to just compile in the terminal

gcc -o program_name program_name.c -lm

lm i believe is a library, this is how you tell the compiler to use the library your program needs

you can find more info about this in this link

[http://www.crasseux.com/books/ctutorial/Libraries.html#Libraries](http://www.crasseux.com/books/ctutorial/Libraries.html#Libraries)

---

### Post by nonewmsgs on 2007-09-06
maybe try taking off the .h.  i know they really dont get used much in c++, and it's worth a shot.

so instead of 
#include <math.h>

try
#include<math>

---

### Post by Rui Pais on 2007-09-07
> **nonewmsgs said:**
> maybe try taking off the .h.  i know they really dont get used much in c++, and it's worth a shot.

so instead of 
#include <math.h>

try
#include<math>

hi,
it's:
```
#include <math.h>
``` for C, and
```
#include <**cmath**>
``` for C++

---


---
title: "Help with gcc compiler"
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by concernicus on 2007-11-01
I have read several other threads and still cant figure out what I'm missing here. I am trying to make a simple program compile it and run it. I have installed the compiler already with the suggested line " sudo apt-get install build essential" and that went fine but when I opened text editor and created this program:

/* THIS PROGRAM JUST DISPLAYS A GREETING */

#include <stdio.h>

void main( void )

{
     puts( "Hello! How are you doing?" );
}

it doesnt compile it just says "warning return type of 'main' is not 'int' "   

I'm currently taking a class on C but I cant figure out whats wrong here, I'm sure its something very obvious.

---

### Post by ghpearson on 2007-11-01
change the line
void main( void )
to 
main ( void )

Its been a while since my C Programming; but it compile in my system :)

---

### Post by Hospadar on 2007-11-01
well, if it just gives a warning, then it did compile.  You can have main return void, but generally the integer return on main is used to indicate the success (or failure) of the program, although for most programs you won't actually need different error codes.

So check to make sure that's the only error you are getting.

Also, I'd be willing to bet that it actually is compiling, you just didn't specify the name of the output file.  The default output executable name is "a.out"

You can specify the name of the executable with the -o option.

something like
gcc -o"yourExecutable" hello.c

and then run it with
./yourExecutable

---


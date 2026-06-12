---
title: "Garbled output from my simple program"
date: 2007-05-24
forum: Absolute Beginner Talk
---

### Post by timdoc1 on 2007-05-24
I have a simple program (for a class) that I have been able to run at school properly:

/* PUBLIC DOMAIN.  BY TOM VAJZOVIC */
#include <pthread.h>
#include <stdlib.h>
#include <stdio.h>
void *thread_func( void *vptr_args );
int main( void ){
  int i, j;
  pthread_t thread;
  pthread_create( &thread, NULL, &thread_func, NULL );
  for( j= 0; j < 20; ++j ){
    fprintf( stdout, "a\n" );
    for( i= 99999999; i; --i );  /* use some CPU time */
  }
  pthread_join( thread, NULL );
  exit( EXIT_SUCCESS );


It just prints out "A"'s and "B"'s to stdio  -worked using Cygwin,

Now I tried it on my NOOB Fiesty install and I get garbage.  Your help is appreciated

Below is the output:
^?ELF^A^A^A^@^@^@^@^@^@^@^@^@^B^@^C^@^A^@^@^@<80><84>^D^H4^@^@^@T^O^@^@^@^@^@^@4^@ ^@^G^@(^@$^@!^@^F^@^@^@4^@^@^@4<80>^D^H4<80>^D^Hà^@^@^@à^@^@^@^E^@^@^@^D^@^@^@^C^@^@^@^T^A^@^@^T<81>^D^H^T<81>^

---

### Post by timdoc1 on 2007-05-24
DIDN"T PASTE THE END OF THE PROGRAM!!!!!  HERE IT IS (FOR CLARITY)

}
void *thread_func( void *vptr_args ){
  int i, j;
  for( j= 0; j < 20; ++j ){
    fprintf( stderr, "  b\n" );
    for( i= 99999999; i; --i );  /* use some CPU time */
  }
  pthread_exit( NULL );
}

---

### Post by Sparkster185 on 2007-05-24
Did you recompile it on your home Feisty machine?

---

### Post by timdoc1 on 2007-05-24
YES.

gcc pthread.c -lpthread

Perhaps I am using the wrong libraries though.  I had a hard time figuring what to use in the PM.

---


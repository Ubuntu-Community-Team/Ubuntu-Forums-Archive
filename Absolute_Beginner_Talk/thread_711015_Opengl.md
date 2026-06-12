---
title: "Opengl"
date: 2008-02-29
forum: Absolute Beginner Talk
---

### Post by madfrenzy on 2008-02-29
Hey, I some help here.
 I was trying to program opengl with c++ on netbeans but the problem is every time I try to run the program (the program works on visual studio) netbeans says 
"Running "/usr/bin/make -f Makefile CONF=Debug" in /media/sda2/projects/C++/pro1/Mad

/usr/bin/make -f nbproject/Makefile-Debug.mk SUBPROJECTS= .build-conf
make[1]: Entering directory `/media/sda2/projects/C++/pro1/Mad'
mkdir -p build/Debug/GNU-Linux-x86
g++ -c -g -o build/Debug/GNU-Linux-x86/mad.o mad.cc
In file included from /usr/include/windef.h:246,
from /usr/include/windows.h:48,
from mad.cc:1:
/usr/include/winnt.h:1964:2: error: #error "undefined processor type"
/usr/include/winnt.h:1966: error: expected initializer before ‘*’ token
/usr/include/winnt.h:1977: error: ‘PCONTEXT’ does not name a type
/usr/include/winbase.h:1500: error: ‘LPCONTEXT’ has not been declared
/usr/include/winbase.h:1855: error: expected ‘,’ or ‘...’ before ‘*’ token
/usr/include/bits/time.h:69: error: redefinition of ‘struct timeval’
/usr/include/winsock2.h:101: error: previous definition of ‘struct timeval’
/usr/include/sys/select.h:78: error: conflicting declaration ‘typedef struct fd_set fd_set’
/usr/include/winsock2.h:56: error: ‘fd_set’ has a previous declaration as ‘typedef struct fd_set fd_set’
/usr/include/sys/select.h:112: error: declaration of C function ‘int select(int, fd_set*, fd_set*, fd_set*, timeval*)’ conflicts with
/usr/include/winsock2.h:611: error: previous declaration ‘int select(int, fd_set*, fd_set*, fd_set*, const timeval*)’ here
mad.cc:32: error: ‘::main’ must return ‘int’
make[1]: *** [build/Debug/GNU-Linux-x86/mad.o] Error 1
make[1]: Leaving directory `/media/sda2/projects/C++/pro1/Mad'
make: *** [.build-impl] Error 2

Build failed. Exit value 2."

I really need to fix this asap cause I've alot of assignments. oh and by the way I'm on ubuntu gutsy 7.10

---

### Post by melopsittacus on 2008-02-29
Hi! This might not be the problem, but are you sure you need to include the Windows headers even if you are programming under Linux?

---

### Post by madfrenzy on 2008-03-01
Yeah because the instructor uses windows and the program must run on visualstudio. is there any other program that can run this code and similar codes as it is(as it would run on visual studio on windows I mean??)

-------------------------------
#include<windows.h>
#include<gl/Gl.h>
#include<gl/glut.h>
void myInit(void) {
    glClearColor(1.0, 1.0, 1.0, 0.0);       // set white background color
    glColor3f(0.0f, 0.0f, 0.0f);          // set the drawing color
    glPointSize(1.0);                 // a 'dot' is 4 by 4 pixels
    glMatrixMode(GL_PROJECTION);
    glLoadIdentity();
    gluOrtho2D(0.0, 640.0, 0.0, 480.0);
}
void myDisplay(void) {
    glClear(GL_COLOR_BUFFER_BIT);      // clear the screen
    int x=5;int y=5;
    do{
        //----------------------------------------------
        int z=y;
        z+=5;
//y+=5;
        //y++;
        do{
            
            
            
            glBegin(GL_POINTS);
            glVertex2i(x, y);          // draw the points
            glEnd();
            glFlush();    // send all output to display
            y++;
        }while (y<=z) ;
        //----------------------------------------------
        do{
            
            
            
            glBegin(GL_POINTS);
            glVertex2i(x, y);          // draw the points
            glEnd();
            glFlush();    // send all output to display
            x++;
        }while (x<=634) ;
        //---------------------------------------------
        
        
        z=y;
        z+=5;
//y+=5;
        //y++;
        do{
            
            
            
            glBegin(GL_POINTS);
            glVertex2i(x, y);          // draw the points
            glEnd();
            glFlush();    // send all output to display
            y++;
        }while (y<=z) ;
        
        
        
        //y+=5;
        do{
            
            
            
            glBegin(GL_POINTS);
            glVertex2i(x, y);          // draw the points
            glEnd();
            glFlush();    // send all output to display
            x--;
        }while (x>=5) ;
        
        //-------------------------------------------
    }while (y<=474) ;
}
void main(int argc, char** argv) {
    glutInit(&argc, argv);          // initialize the toolkit
    glutInitDisplayMode(GLUT_SINGLE | GLUT_RGB); // set display mode
    glutInitWindowSize(640, 480);     // set window size
    glutInitWindowPosition(100, 150); // set window position on screen
    glutCreateWindow("MAD lOOP"); // open the screen window
    glutDisplayFunc(myDisplay);     // register redraw function
    myInit();
    glutMainLoop();                 // go into a perpetual loop
}

------------------------------------------------------------

---


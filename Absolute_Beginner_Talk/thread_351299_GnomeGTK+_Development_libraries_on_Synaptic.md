---
title: "Gnome/GTK+ Development libraries on Synaptic"
date: 2007-02-01
forum: Absolute Beginner Talk
---

### Post by andrew222 on 2007-02-01
Hello,

I would like to get the Gnome/GTK+ development libraries for Ubuntu. 

I've tried to install four different libraries from source but get errors when I run 'make install'.  It seems like a pit of problems and would like to get them on Synaptic before doing any troubleshooting...

What are the names of the files needed to run a gnome/GTK+ application on Synaptic package manager?  Hope someone can help me out :-)

Andrew

---

### Post by po0f on 2007-02-02
andrew222,

[libgtk2.0-dev](http://packages.ubuntu.com/edgy/libdevel/libgtk2.0-dev) and [libgnome2-dev](http://packages.ubuntu.com/edgy/libdevel/libgnome2-dev) should get you compiling.

---

### Post by andrew222 on 2007-02-02
Thank you very much,  I will get those and try again.

I really do appreciate it.

Andrew

---

### Post by andrew222 on 2007-02-02
I downloaded those and ran an introductory code example on Emacs and it worked perfectly.  In the boo it gives a command line to use and I get a bunch of errors.

Here is the code.  It is from 'Beginning Linux programming (Matthew/Stones') , chapter 16, pg. 631

-------------------------------------------
/* The first example is a simple gtk+ program to get us started.
   gtk+ is first initialised, a gtkwindow widget created, and shown.
   gtk_main is called to begin the processing loop */

#include <gtk/gtk.h>

int main (int argc, char *argv[])
{
  GtkWidget *window;

  gtk_init(&argc, &argv);
  window = gtk_window_new(GTK_WINDOW_TOPLEVEL);
  gtk_widget_show(window);
  gtk_main ();

  return 0;
}  
---------------------------------------------------------------


The book says to use this command line 

gcc gtk1.c gtk1 'pkg-config -cflags -libs gtk+2.0'

I use it and get these errors

andrew@Ubuntu-one:~/buddha/chapter16$ gcc gtk1.c gtk1 'pkg-config -cflags -libs gtk+2.0'
gcc: pkg-config -cflags -libs gtk+2.0: No such file or directory
gtk1.c:5:21: error: gtk/gtk.h: No such file or directory
gtk1.c: In function ‘main’:
gtk1.c:9: error: ‘GtkWidget’ undeclared (first use in this function)
gtk1.c:9: error: (Each undeclared identifier is reported only once
gtk1.c:9: error: for each function it appears in.)
gtk1.c:9: error: ‘window’ undeclared (first use in this function)
gtk1.c:12: error: ‘GTK_WINDOW_TOPLEVEL’ undeclared (first use in this function)



I run it on emacs and I get a clean compile....it generated a command line to run the code

gcc -Wall -o gtk1 gtk1.c 'pkg-config --cflags --libs gtk+-2.0'

I try using this command and get this error message...

andrew@Ubuntu-one:~/buddha/chapter16$ gcc -Wall -o gtk1 gtk1.c 'pkg-config --cflags --libs gtk+-2.0'
gcc: pkg-config --cflags --libs gtk+-2.0: No such file or directory
gtk1.c:5:21: error: gtk/gtk.h: No such file or directory
gtk1.c: In function ‘main’:
gtk1.c:9: error: ‘GtkWidget’ undeclared (first use in this function)
gtk1.c:9: error: (Each undeclared identifier is reported only once
gtk1.c:9: error: for each function it appears in.)
gtk1.c:9: error: ‘window’ undeclared (first use in this function)
gtk1.c:11: warning: implicit declaration of function ‘gtk_init’
gtk1.c:12: warning: implicit declaration of function ‘gtk_window_new’
gtk1.c:12: error: ‘GTK_WINDOW_TOPLEVEL’ undeclared (first use in this function)
gtk1.c:13: warning: implicit declaration of function ‘gtk_widget_show’
gtk1.c:14: warning: implicit declaration of function ‘gtk_main’
andrew@Ubuntu-one:~/buddha/chapter16$ 


My question is,  how come it can compile perfectly on Emacs, but when I compile it by command line I get errors, especially the "gtk1.c:5:21: error: gtk/gtk.h: No such file or directory"

Can someone help me out?

Thanks again,


Andrew

---

### Post by po0f on 2007-02-04
andrew222,

The console command should have been:
```
[FONT="Courier New"]$ gcc gtk1.c -o gtk1 **`**pkg-config -cflags -libs gtk+2.0**`**[/FONT]
```

Note that those are backticks (left of the 1 on a QWERTY keyboard), not single quotes.  Using the backticks will solve your "gtk/gtk.h not found" error.

---

### Post by chavo on 2007-02-04
That still won't compile it, use this line instead.
```
gcc gtk1.c -o gtk1 `pkg-config --cflags --libs gtk+-2.0`
```

---

### Post by andrew222 on 2007-02-04
Thank you, I should have looked into that! :-)

---

### Post by YourSurrogateGod on 2008-04-14
Here is my make file.
```
all: simpleWindow
simpleWindow: simpleWindow.o
	g++ -o simpleWindow `pkg-config --clfags --libs gtk+-2.0` simpleWindow.o

simpleWindow.o: simpleWindow.cpp
	g++ -c -g -fno-inline -Wall simpleWindow.cpp

clean:
	rm simpleWindow simpleWindow.o
```
My program is no different from what is mentioned above. I get the same error saying that gtk/gtk.h is not found. The problem is probably dependent on where I put the pkg-config in the file. Thing is, I've tried sticking it everywhere, but still nothing comes of it.

---


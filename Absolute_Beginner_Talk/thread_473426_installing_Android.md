---
title: "installing Android"
date: 2007-06-14
forum: Absolute Beginner Talk
---

### Post by LykkeLamaen on 2007-06-14
Hello,
I'm quite new to both Ubuntu and the Linux world in general, but I try my best.
I hope this is the right place for my question

I'm trying to install a program called android [http://www.wildopensource.com/activities/larry-projects/android.php]("http://www.wildopensource.com/activities/larry-projects/android.php")
and so far I have downloaded the .tzp, unpacked it in my home folder, and tried to read and understand the README file. It says
[INDENT]Unpack the archive and type "./configure --prefix=<dir>" where <dir>
is the directory where you have installed the tcl/tk you wish to use
with android - usually (though not always) this is /usr, though if
you often compile your own versions it may be /usr/local or some
other directory.  This will create the make file. [B]Type  "make" at
the top of the hierarchy to build the program.[/B]  "make install" will
install the program and its utilities where you need them.  You may
need to be root to accomplish the install..[/INDENT]

So I typed ./configure --prefix=/usr
No problem. But the next part? "make" at the top of the hierarchy? I tried just to type make, but I got a page full of errors. 
As far as I can tell I've already installed tcl and tk, as it appears that Android depends on them.

I hope I have provided enough info. Slap me with a trout and tell me what you need to know if this wasn't enough.

---

### Post by jiminycricket on 2007-06-14
You probably need the packages build-essential (compiler) and xserver-xorg-dev as well.

More info: [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by LykkeLamaen on 2007-06-14
installed both, but alas, it didn't change a thing.
What confuses me is what the README means when it tells me to Type "make" at the top of the hierarchy.
Where is the top of the hierarchy? Is that the ~/android folder? Or the /usr folder?

---

### Post by LykkeLamaen on 2007-06-14
This is my Complete Terminal session

```

primdal@primdal-ubuntu:~$ cd android/
primdal@primdal-ubuntu:~/android$ ./configure --prefix=/usr/
primdal@primdal-ubuntu:~/android$ make
cp android.tcl android
cc -g -shared -fPIC -o android.so -L/usr/X11R6/lib -ltk -ltcl -lXtst -lXext -lXmu -lX11 -lm android.c 
android.c:21:29: error: X11/Xmu/WinUtil.h: No such file or directory
android.c:22:16: error: tk.h: No such file or directory
android.c: In function ‘send_xeventsCmd’:
android.c:119: fejl: expected declaration specifiers before ‘ClientData’
android.c:120: fejl: expected declaration specifiers before ‘Tcl_Interp’
android.c:132: fejl: ‘TCL_OK’ undeclared (first use in this function)
android.c:132: fejl: (Each undeclared identifier is reported only once
android.c:132: fejl: for each function it appears in.)
android.c:142: fejl: ‘TCL_ERROR’ undeclared (first use in this function)
android.c: In function ‘TidyUp’:
android.c:226: fejl: expected declaration specifiers before ‘ClientData’
android.c:227: fejl: expected declaration specifiers before ‘Tcl_Interp’
android.c: In function ‘dispinfoCmd’:
android.c:256: fejl: expected declaration specifiers before ‘ClientData’
android.c:257: fejl: expected declaration specifiers before ‘Tcl_Interp’
android.c:303: fejl: ‘TCL_ERROR’ undeclared (first use in this function)
android.c:352: fejl: ‘TCL_VOLATILE’ undeclared (first use in this function)
android.c:374: fejl: ‘TCL_OK’ undeclared (first use in this function)
android.c: In function ‘pick_windowCmd’:
android.c:394: fejl: expected declaration specifiers before ‘ClientData’
android.c:395: fejl: expected declaration specifiers before ‘Tcl_Interp’
android.c:421: fejl: ‘TCL_ERROR’ undeclared (first use in this function)
android.c:442: fejl: ‘TCL_VOLATILE’ undeclared (first use in this function)
android.c:443: fejl: ‘TCL_OK’ undeclared (first use in this function)
android.c: In function ‘win_idCmd’:
android.c:462: fejl: expected declaration specifiers before ‘ClientData’
android.c:463: fejl: expected declaration specifiers before ‘Tcl_Interp’
android.c:481: fejl: ‘TCL_ERROR’ undeclared (first use in this function)
android.c:542: fejl: ‘TCL_VOLATILE’ undeclared (first use in this function)
android.c:543: fejl: ‘TCL_OK’ undeclared (first use in this function)
android.c: In function ‘compress_timeCmd’:
android.c:559: fejl: expected declaration specifiers before ‘ClientData’
android.c:560: fejl: expected declaration specifiers before ‘Tcl_Interp’
android.c:567: fejl: ‘TCL_ERROR’ undeclared (first use in this function)
android.c:573: fejl: ‘TCL_VOLATILE’ undeclared (first use in this function)
android.c:578: fejl: ‘TCL_OK’ undeclared (first use in this function)
android.c: In function ‘widgetregCmd’:
android.c:594: fejl: expected declaration specifiers before ‘ClientData’
android.c:595: fejl: expected declaration specifiers before ‘Tcl_Interp’
android.c:608: fejl: ‘TCL_ERROR’ undeclared (first use in this function)
android.c:632: advarsel: incompatible implicit declaration of built-in function ‘malloc’
android.c:691: advarsel: incompatible implicit declaration of built-in function ‘malloc’
android.c:734: fejl: ‘TCL_VOLATILE’ undeclared (first use in this function)
android.c:735: fejl: ‘TCL_OK’ undeclared (first use in this function)
android.c: In function ‘Android_Init’:
android.c:749: fejl: expected declaration specifiers before ‘Tcl_Interp’
android.c:754: advarsel: incompatible implicit declaration of built-in function ‘malloc’
android.c:777: fejl: ‘TCL_OK’ undeclared (first use in this function)
make: *** [android.so] Fejl 1

```

I'm danish so it translates some of the error messages:
fejl means error
advarsel means warning

I hope it is more readable to someone else than it is to me.
I have no idea what needs to be done

---


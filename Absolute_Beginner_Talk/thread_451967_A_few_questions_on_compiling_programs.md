---
title: "A few questions on compiling programs"
date: 2007-05-22
forum: Absolute Beginner Talk
---

### Post by Belliinator on 2007-05-22
Well, I have tried to compile a variety of programs in linux from source code, and aprt from mpg123 and SDL libraries, i have failed. I have a magazine DVD full of applliations only for Linux, so I would like to learn more.

1. When compiling a file, should I untar and compile straight on to the open file system, or does it have tto be untared to my home folder or to Usr/bin etc? For libraries such as Glib does it matter, because Glib does not work.

2. Once you have compiled the application, where do you run it?

3. What do you do about errors while running make that do not mean anything.

4. Which is better X11 or SVGALib, and does Ubuntu already contain X11. Because various games to not see that i tried to compile in the home folder.

It is really starting to annoy me. I know you can download applications through synaptic, but I have dial-up at home but broadband here where I can download applications and bring them home, plus I have that DVD. Please help

---

### Post by blind0wl on 2007-05-22
1.  Untar in any directory you wish, it does not matter...I usually put them in /opt and keep them there.

2.  Once you have compiled the program, you will need to search for its runnable name...you can either look for the program by doing a find / -name 'program' or watch the make and see where its putting it.  The program can go into multiple different directorys and your PATH should have most of the more common ones all ready there.

3.  If the errors dont stop make, then don't worry about them too much.

4.  Ubuntu all ready contains X11.

Cheers

Blindy

---

### Post by Belliinator on 2007-05-22
-The errors do stop make, writing obscure messages such as error 1

-How do I get the programs to find X11 

Thankyou for your help so far.

---

### Post by blind0wl on 2007-05-22
When you get the make errors, you will usually see the issue its having a couple of lines before the error, most make issues are because the program is relying on something being there when its not.  Generally I will google search the problem line to see what I need to compile before it.

Can you elaborate on the X11 question a bit more?  Are you getting errors when trying to run games etc?

---

### Post by Belliinator on 2007-05-22
checking for XOpenDisplay in -lX11... no
checking for gl_putbox in -lvgagl... no
configure: error: "Found neither SVGA nor X on your system."

This is for lincity, but other applications do this as well

---

### Post by blind0wl on 2007-05-22
What version of Ubuntu are you running?  Do you have a GUI such as gnome or KDE that you can run?

Cheers

Blindy

---

### Post by Belliinator on 2007-05-24
Im running Ubuntu 6.06 dapper drake and I do not have KDE at all.

Isn't Gnome the default?

---

### Post by Bachstelze on 2007-05-24
You have X11. Now, if you told us a bit more precisely what you're trying to do, we could maube help you...

---

### Post by Belliinator on 2007-05-24
I want the programs that keep on complaining during compilation to stop whining that cannot find SDL, GLib, X11 etc. When all these are supposedly installed

THe games see SDL, but can't run for some bizzare reason. THey cant see the X11 video libraries it sounds like, and when i try to compile XMMS of the DVD it does not see GLib when Im pretty sure I installed it.

SDL libraries, GLib are installed on the open file system is this wrong?

---

### Post by Bachstelze on 2007-05-24
Did you install the -dev files for them as well ?

---

### Post by Belliinator on 2007-05-24
I dont think so. What are they? 
How do you do that.

---

### Post by Bachstelze on 2007-05-24
Install the package with the name of the thing with -dev at the end. For exemple, for glib, it would be *libglib-dev*.

---

### Post by toasterofirony on 2007-05-24
They are just developer parts of libs etc. required for compiling programs.

[editus ninjatus] Oops, beat'd. By the way, for compiling Checkinstall is quite handy as it'll make your program into  a tasty .deb for easy install/ removal.

---


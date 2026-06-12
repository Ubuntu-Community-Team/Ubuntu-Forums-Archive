---
title: "ok so installed a program but where did it go?"
date: 2006-08-07
forum: Absolute Beginner Talk
---

### Post by DesertFox on 2006-08-07
i installed with the packege manager but where do i find it so i can start it

---

### Post by lazyd2 on 2006-08-07
What did you install?

---

### Post by davebgimp on 2006-08-07
> **DesertFox said:**
> i installed with the packege manager but where do i find it so i can start it

Try hitting ALT + F2 and typing in the program name.

---

### Post by DesertFox on 2006-08-07
its wine by the way and it wants a C:/windows/system32/ dic?

---

### Post by davebgimp on 2006-08-07
Okay.. don't know about that, but I can tell you that the first thing you want to do is open a terminal and run **winecfg** to get things set up.

To install or run a windows program, you type **wine /path/to/program.exe** in a terminal.

Also, the next time you reload your menu (Gnome or KDE) Wine should show up in your program lists, giving you a gui option for launching programs with it.

Hope that helps some.

---

### Post by DesertFox on 2006-08-07
it does'nt appear but.. can you explain the terminal command a little better??

---

### Post by Upochapo on 2006-08-07
for the commandline:

winecfg all by itself sets up wine and creates a virtual c drive to install window applications.

to install a windows application you have to know the location of the file. so to run an install.exe for say like installing Diablo II from a cd, you would type something like this

wine /media/cdrom0/install.exe  

now, if you cannot find the windows app u installed right away, it can be tricky to find.  In your home directory (open a filebrowser window (nautilus)), and in the menu bar, click on view, then show hidden files.  scroll through the file window til you find a folder title .wine  Here is where ur windows programs will be installed to.

hope this helps.

---


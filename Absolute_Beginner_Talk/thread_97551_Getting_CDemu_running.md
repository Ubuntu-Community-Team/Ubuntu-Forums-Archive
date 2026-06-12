---
title: "Getting CDemu running"
date: 2005-12-01
forum: Absolute Beginner Talk
---

### Post by Grafster on 2005-12-01
Does anyone know how to get CDemu ([http://cdemu.sourceforge.net/](http://cdemu.sourceforge.net/)) or a similar sort of program running?

It seems like you need to play around with bz2 files. Which doesn't sound so bad, unzip and run or something but its a bit tougher than this whole dpkg thing.

---

### Post by frodon on 2005-12-01
I use cdemu without any problems, just follow the instructions to install it.
Here it's not a debian package you have but the source code so you have to compile it and it's really easy, just follow the instruction in the link. However check that you have the build-essential package installed before installing cdemu, this package contain all the needed tools to compile a software from sources.

---

### Post by Grafster on 2005-12-02
I really don't mean to sound whiny but the instructions assume higher level of Linux comprehension than I (or most non-programmers) have.

The first line works fine.

Line 2
> checkout the code from cvs:
> $ cvs -z3 -d:pserver:anonymous@cvs.sourceforge.net:/cvsroot/cdemu co -P cdemu
Above and beyond my having no idea what we're checking out Ubuntu doesn't know what cvs is.

Line 3
> you need the source of your current running kernel.
> /lib/modules/$(shell uname -r)/build/include needs to point at it.
Source? Point? this isn't a command name, I can dig around in the file but that sounds like a cronictly bad idea since I don't know what file this is.

Line 4
>make
returns: 
make: *** No rule to make target `cdemu.ko', needed by `modules'.  Stop.

(probably since I skipped the two lines before that).

I appriciate that the directions on the page do, in some kind of high level manner, communicate what needs to happen for CDemu to work. But they aren't instructions in the sense that you can follow them an achieve the desired outcome: (i.e. having CDemu work).

---

### Post by frodon on 2005-12-03
Strange, i didin't get any problems at the time when i compiled it. So i give you the .deb i made at the bottom of the post. To install it, remove the .bz2 extension and run this command :  ```
sudo dpkg -i cdemu-0.7_0.7-1_i386.deb
```To use cdemu follow the steps 5 and 6 of the [link]("http://cdemu.sourceforge.net/").

---

### Post by neonlug on 2005-12-05
I have cdemu running, but why do I have to enter modprobe cdemu everytime I boot to get it to work?

---

### Post by frodon on 2005-12-05
I think it's because cdemu use the modprobe kernel module to perform the emulation and therefore it can't work without it loaded, maybe someone could confirm that.

---

### Post by Gray. on 2005-12-05
You could try:
System > Preferences > Sessions
"Startup Programs" Tab > Add
Startup Command: modprobe cdemu
Order: 50 > OK > Close

When you login next time it should automatically run the command for you.

**NOTE:**
If your system refuses to go past the Ubuntu Splash Screen (the one that shows Nautilus, Metacity etc. loading), then login using a "Failsafe Gnome" Session, and remove the entry you made in System > Preferences > Sessions.

---

### Post by neonlug on 2005-12-05
Can I just load the cdemu at boot time?

---

### Post by Neg127 on 2005-12-09
Yes you can load the module at boot time.  Just simply add the module to your /etc/modules.

Then the next time you rebote you will not have to modprobe the module.

Neg127

---

### Post by mondi0924 on 2005-12-09
Got a problema running modprobe on cdemu , it says that module cdemu not found. I tried running sudo modprobe -l cd* it does not show up. what could be causing this problem? any suggestions?

---


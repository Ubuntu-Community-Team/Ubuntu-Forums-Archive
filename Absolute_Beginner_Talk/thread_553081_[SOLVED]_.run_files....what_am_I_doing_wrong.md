---
title: "[SOLVED] .run files....what am I doing wrong?"
date: 2007-09-17
forum: Absolute Beginner Talk
---

### Post by stewils on 2007-09-17
Ok, had a quick search, couldn't find the answer, though it's probably out there.
My problem is ultra noob and is as follows:
Downloaded the latest ATI drivers ati-driver-installer-8.41.7-x86.x86_64.run to my desktop.
Double click/ press enter on it when highlighted....nothing happens.
What do I do with a .run file?

---

### Post by wolfger on 2007-09-17
> **stewils said:**
> Ok, had a quick search, couldn't find the answer, though it's probably out there.
My problem is ultra noob and is as follows:
Downloaded the latest ATI drivers ati-driver-installer-8.41.7-x86.x86_64.run to my desktop.
Double click/ press enter on it when highlighted....nothing happens.
What do I do with a .run file?

I'm not sure if double-click should work or not. I always do these things from the command line.

Open a console, cd to the desktop directory, and type ```
./ati-driver-installer-8.41.7-x86.x86_64.run
```
If it still doesn't work, you should at least see some output on the console that will help us determine the problem... paste that output here, and we'll see what we can do.

---

### Post by wirelessmonkey on 2007-09-17
open a terminal and cd to the directory where your .run file is hiding.  Then:
sudo ./ati-driver-installer-8.41.7-x86.x86_64.run

---

### Post by Shazaam on 2007-09-17
Or you can go here....
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

and scroll down to install from ati/amd.

---

### Post by stewils on 2007-09-17
OK,
Followed the tutorial until:
> After installing the kernel source and xorg driver, you will now need to compile the fglrx kernel module in order to get 3-d rendering. Do so with the following commands:

sudo m-a prepare,update 
sudo m-a build,install fglrx-kernel (or module-assistant -f to force a rebuild if needed)
sudo depmod
sudo rm -f /usr/src/fglrx-kernel*.deb


Did sudo m-a prepare,update no problem but then
sudo m-a build,install fglrx-kernel 
Gives this:
> ste@ste-laptop:~$ sudo m-a build,install fglrx-kernel
The source tarball could not be found!
Package fglrx-kernel-src not installed?
Running "m-a -f get fglrx-kernel-src" may help.
find: /usr/src/modules: No such file or directory
and a Module Assistant log file saying:
 > Build log starting, file:                                                  &#8593; 
 &#9474; /var/cache/modass/fglrx-kernel-src.buildlog.2.6.20-16-generic.1190071607
Running m-a -f get fglrx-kernel-src gives me:
 > You are not root and no replacement directory (the -u option) is   &#8593;     
     &#9474; specified. Unable to continue.

And running module-assistant -f gives me the same.

And I think thats this is the build log, but it could just be the error message telling me that I don't know how to open it.....

ste@ste-laptop:/var/cache/modass$ fglrx-kernel-src*buildlog*
bash: fglrx-kernel-src.buildlog.2.6.20-16-generic.1190071132: command not found

---

### Post by stewils on 2007-09-18
bump

---

### Post by Maestro23 on 2007-09-18
> **stewils said:**
> bump

Since you don't have a grasp on terminal/commands yet, try using the Envy script to install your driver.

Envy script: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Good luck.

---

### Post by stewils on 2007-09-18
> Envy script: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)


Will nvida scripts work with?  My graphics card is ATI....

---

### Post by Maestro23 on 2007-09-18
> **stewils said:**
> Will nvida scripts work with?  My graphics card is ATI....

It works for BOTH.

Read #1 under "What is Envy"

---

### Post by stewils on 2007-09-18
yep, thats hit the spot.  Things seem to be running a little quicker now.
Cheers

---

### Post by Maestro23 on 2007-09-18
> **stewils said:**
> yep, thats hit the spot.  Things seem to be running a little quicker now.
Cheers

Good deal man.  Don't forget to mark this thread SOLVED.

---


---
title: "partitioning"
date: 2005-09-10
forum: Absolute Beginner Talk
---

### Post by nighttime on 2005-09-10
I'm running Windows XP home edition and I wanna make room for ubuntu, but I'm not really sure how to do it... when I get to the disk partition step in the installation there's just 2 partitions, #1 primary 40GB ntfs something... and another one that's 8.4MB (FREE SPACE) but apparently it's not enough for Ubuntu.

I have a 40 GB hard drive, I'm currenly using only about 3GB and I wanna split the 40GB in two so I can have Windows in one partition and Ubuntu on another.

The problem is I have no idea how to do this... and I don't wanna mess my HD up or anything. Is there a guide I can consult or something? Or can anyone please help me w this?

---

### Post by Wolki on 2005-09-10
[QUOTE=nighttime]The problem is I have no idea how to do this... and I don't wanna mess my HD up or anything. Is there a guide I can consult or something? Or can anyone please help me w this?[/QUOTE]

Here you go: [https://wiki.ubuntu.com/forum/installation/Partitioning](https://wiki.ubuntu.com/forum/installation/Partitioning)

If you have additional questions, feel free to ask.

---

### Post by az on 2005-09-10
[QUOTE=nighttime]I' and another one that's 8.4MB (FREE SPACE) but apparently it's not enough for Ubuntu.
[/QUOTE]


Indeed!  MB is megabytes and GB is gigabytes.  Somebody already filed a bug report about this...

---

### Post by nighttime on 2005-09-10
THANX! =D I'm writing this using ubuntu! Whee!

Now I can't change my screen resolution though, its stuck in 640x480 (TOO BIG)... damn... I downloaded the right driver but I can't install it >_< something about modules not being compiled oh well... I'll find the solution to that later.

So it's a bug huh... cool, I found a bug =D

---

### Post by aysiu on 2005-09-10
[QUOTE=nighttime]
Now I can't change my screen resolution though, its stuck in 640x480 (TOO BIG)... damn... I downloaded the right driver but I can't install it >_< something about modules not being compiled oh well... I'll find the solution to that later.[/QUOTE] Or you could find it now: 

[http://ubuntuforums.org/showthread.php?t=21984](http://ubuntuforums.org/showthread.php?t=21984)

---

### Post by nighttime on 2005-09-10
That didn't work... the xorg.conf file already had all resolutions... so I tried deleting every one of them except "1024x768" and rebooting :P Wich didn't work... so I'm still stuck with annoyingly big 640x480

I have the precise driver for my graphics card but I can't install it >_< here's the error messages I get, in case anyone knows anything about this:

DIRECT RENDERING OPEN SOURCE PROJECT  -  DRIVER INSTALLATION SCRIPT

[ [http://dri.sourceforge.net](http://dri.sourceforge.net) ]

==========================================================================

The script will now compile the agpgart module and DRM kernel modules
for your machine.

Press ENTER to continue or CTRL-C to exit.


Compiling new agpgart module...

ERROR: AGPGART module did not compile

Compiling DRM module...

ERROR: Kernel modules did not compile

The DRI drivers can not be installed without the latest kernel modules.
Installation will be aborted. See the dri.log file for information on
what went wrong.


This is the dri.log file's contents:


make -C /lib/modules/2.6.10-5-386/build SUBDIRS=/home/oscarmier/Desktop/dripkg/agpgart-2.0 modules
make: *** /lib/modules/2.6.10-5-386/build: No such file or directory.  Stop.
make: *** [default] Error 2
Makefile.linux:151: *** Cannot find a kernel config file.  Stop.


Ok, so at first the installation didn't get that far, it just said something about not being able to compile stuff, so I installed some compilers (build-essential) from the synaptic package manager and I got this far, but I don't know what to do about the  inexistant /lib/modules/2.6.10-5-386/build file/directory... help? please?

---

### Post by aysiu on 2005-09-10
What about adjusting the HorizSync and VertRefresh ranges?

[http://ubuntuforums.org/showpost.php?p=129379&postcount=21](http://ubuntuforums.org/showpost.php?p=129379&postcount=21)

---

### Post by nighttime on 2005-09-11
Yeah, heh, that worked *blush* :-P  Thanx alot!

---


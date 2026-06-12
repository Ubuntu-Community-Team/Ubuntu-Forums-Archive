---
title: "Is it possible to use the Darwin terminal in a Linux box"
date: 2007-05-18
forum: Apple Intel Users
---

### Post by cocotu on 2007-05-18
I guess my question is the same as the Title:

Is it possible to use the Darwin terminal in a Linux box.  I know I can do ssh to the Mac computer.  What I mean can I somehow have or install the Darwin terminal in my ubuntu box?  I want this because at work we use a Mac Server and at home a have my ubuntu box, but wanted to practice a few commands that are unique to Darwin at home.  Is this possible?

thanks

---

### Post by msgyrd on 2007-05-19
I don't know exactly what you're asking, Darwin is a completely seperate operating system.  If you're not running a Mac at home, and you just want to test Darwin commands locally, you could download VirtualBox from the repositories and install the Darwin base system inside a virtual machine.

[http://www.opensource.apple.com/darwinsource/](http://www.opensource.apple.com/darwinsource/)

I have no experience running Darwin by itself, so my knowledge ends there.

---

### Post by cocotu on 2007-05-21
Thanks but VirtualBox does not support Mac OS or I misread the info.  thanks

---

### Post by DJ_Max on 2007-05-21
What commands are Darwin specific? Or at least name a few.

---

### Post by cocotu on 2007-10-03
All Darwin commands.

---

### Post by cyberdork33 on 2007-10-03
> **cocotu said:**
> Thanks but VirtualBox does not support Mac OS or I misread the info.  thanks
If you need Full OSX then no you cannot install it to VirtualBox. But if you only are concerned with Darwin, it is a UNIX system and will run fine on both a normal PC and many Virtual Machines. 

What commands are you referring to specifically. Many commands are the same in Linux as in Darwin, and thus ALL Darwin commands are not Darwin specific.

---

### Post by russell.h on 2007-10-04
Most commands that you use in a terminal on a mac should carry over to Linux. A "command" is really just a program that you are running from the command line, and a lot of the utilities that Apple includes with OS X are actually the same ones as are included with Ubuntu (ie, when you use ssh from a Mac you are using OpenSSH, the same as with Ubuntu). So for the most part the only difference that you should notice between OS X and Linux from a terminal is that Apple went and mutilated their file system a bit (/Users = /home, etc).

Thats why when I needed a laptop I got a Mac. It gets better battery life than most laptops running Linux, but I get a nearly identical command line.

---

### Post by cocotu on 2007-10-04
thanks Russell.h!! I was just curious!

---

### Post by russell.h on 2007-10-04
Any time.

---


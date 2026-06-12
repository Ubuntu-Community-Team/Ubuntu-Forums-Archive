---
title: "Ubuntu from Suse"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by Flash319 on 2007-03-13
I am new to Linux as mos on this forum.  I bought a 1ghz computer for my shop and plan to run EMC cnc software on it.  The computer has Suse on it and I can get into anything as I need a password to get into anything or even log in.  I tryed booting off a windows disk but it just ignores the disk and continues to boot Suse. 

I had some problems getting ubuntu 6.06 but think I have a good copy now.  Will the Ubunt disk format the drive before it installs onto the drive?  Does anyone know how I can break into the Suse OS?  I was hoping I could save the drivers and stuff that are in there and use them for Ubuntu to save me having to hunt them down later.

---

### Post by jdfreshwater on 2007-03-13
I don't know how to break into suse, but it sounds like you may need to change your bios settings in order to boot from CD, it may just be booting directly from the hard drive first.  Ubuntu will probably need to reformat the partition that the operating system will reside, as ubuntu does not follow the same scheme as Suse in installing software.  As far as drivers, you may be best off just installing new drivers, most should become active upon install.  The Ubuntu disk should boot to a live environment before installing, so you may be able to save some files.

---

### Post by lamalex on 2007-03-13
if its skipping the windows cd and going right into suse then you need to change your bios to boot from cd first. once that's done you will be able to boot intu ubuntu, get any files you want while in the live environment, and then install and format your hdd.

---

### Post by Flash319 on 2007-03-13
It is booting from the CD because if I put in the Ubuntu CD it will boot to the Ubunt install menu but when I go to install I get an "Error reading IO" which I think is a bad download of the ISO.  I do not know why the windows disk will not pick up when I use it.

Anyway I downloaded a new Ubuntu and am going to try to install tonight.  Hopefuly it goes well.  Is there a list of commands that Ubuntu (linux) uses that I can look at.  I used to mess around with Dos when it was the only system in town, are Linux commands similar?

---

### Post by RedSquirrel on 2007-03-15
> **Flash319 said:**
> It is booting from the CD because if I put in the Ubuntu CD it will boot to the Ubunt install menu but when I go to install I get an "Error reading IO" which I think is a bad download of the ISO.  I do not know why the windows disk will not pick up when I use it.

Anyway I downloaded a new Ubuntu and am going to try to install tonight.  Hopefuly it goes well.  Is there a list of commands that Ubuntu (linux) uses that I can look at.  I used to mess around with Dos when it was the only system in town, are Linux commands similar?


I hope your install of Ubuntu went well.

Here is a list of commands:

[http://www.oreillynet.com/linux/cmd/](http://www.oreillynet.com/linux/cmd/)

I would also recommend the guides at  The Linux Documentation Project:

[http://tldp.org/guides.html](http://tldp.org/guides.html)

You probably won't have to use the command line too often (unless you're like me and you really like it!). There are graphical interfaces for most things these days. However, using the command line is a very powerful way to get things done without all that pointing and clicking. I use it all the time. In fact, when I sit down in front of my linux box, the terminal is the first thing I open and the last thing I close. :)

Your DOS experience will help you somewhat. The commands in linux are different, and there are more of them, but at least the idea of typing commands at a prompt will be familiar to you. (a very simple example: you use **ls** in linux instead of **DIR**).

In a terminal you can also get information about any command by consulting the man pages:

```
man <command>
```You might also want to consider picking up a copy of "Linux in a Nutshell" or something similar. I have an old copy of "UNIX in a nutshell" that comes in handy once in a while.

---


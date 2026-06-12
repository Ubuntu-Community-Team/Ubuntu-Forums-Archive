---
title: "Any tutorials..."
date: 2007-12-18
forum: Absolute Beginner Talk
---

### Post by SegaFan on 2007-12-18
Hi, I've been using Linux for just 3 days and so obviously I know very little. I want to learn. Are there any good online tutuorials that'll teach me the basics of using Ubuntu/Linux, for instance the ins and outs of the command line, where I'm completely lost.

So far I've managed to do quite a lot by trial and error, and with help from this forum (which has been great), but I'd like to actually know what I'm doing.

---

### Post by aysiu on 2007-12-18
Start here:
[http://www.psychocats.net/ubuntu](http://www.psychocats.net/ubuntu)

---

### Post by daimaru on 2007-12-18
here you go try these links.
[http://ubuntuguide.org/wiki/Ubuntu:Gutsy](http://ubuntuguide.org/wiki/Ubuntu:Gutsy)
well it defauts to gutsy now, but the feisty one has a bit more info. so you can go here too.
[http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty)

[http://howtoforge.com]("http://howtoforge.com/")
on howtoforge just click ubuntu and check all the howto's to your liking.

---

### Post by discoade on 2007-12-18
you could have a look here [https://help.ubuntu.com/](https://help.ubuntu.com/)

plenty of reading there so far!

---

### Post by x-to-tha-t on 2007-12-18
For general linux tutorials rather than just ubuntu you can use
[www.linux-tutorial.info/](www.linux-tutorial.info/)
I will warn though - Linux is heavy going - expect to have to learn a lot in a short space of time. Also one big hint - you will almost never have to reinstall the OS - you can fix everything you break!

---

### Post by bodhi.zazen on 2007-12-18
first, welcome to Ubuntu.

What do you want to learn ?

Terminal commands ? (try the last first [http://linuxcommand.org/](http://linuxcommand.org/))

Command line tips:
	[http://www.pixelbeat.org/cmdline.html](http://www.pixelbeat.org/cmdline.html)
	[http://www.justlinux.com/nhf/Command_Reference](http://www.justlinux.com/nhf/Command_Reference)
	[http://www.ss64.com/bash/](http://www.ss64.com/bash/)

[http://www-128.ibm.com/developerworks/aix/library/au-badunixhabits.html?ca=lnxw01GoodUnixHabits](http://www-128.ibm.com/developerworks/aix/library/au-badunixhabits.html?ca=lnxw01GoodUnixHabits)

			

Commands
	[http://www.unixguide.net/linux/linuxshortcuts.shtml](http://www.unixguide.net/linux/linuxshortcuts.shtml)
	[http://www.reallylinux.com/docs/admin.shtml](http://www.reallylinux.com/docs/admin.shtml)
	[http://www.reallylinux.com/docs/guru.shtml](http://www.reallylinux.com/docs/guru.shtml)
	[http://linuxcommand.org/](http://linuxcommand.org/)

---

### Post by mellowd on 2007-12-18
There is tons of documentation out there, it can be difficult to know where to start. This is pretty good: linuxcommand.org

You can also check my blog in my sig for some more reading

---

### Post by bcrom on 2007-12-18
I felt like this when I first started using Linux.  My best advice: be patient.  You obviously are willing to learn, so you will.  It won't happen all at once, but in a couple months you'll feel like a pro.

---

### Post by Johnny3 on 2007-12-18
This is one like.
[http://screencasts.ubuntu.com/](http://screencasts.ubuntu.com/)

Johnny3
Gainesville, Fl

---

### Post by SegaFan on 2007-12-18
Thank you everyone, that's all really helpful. I will have a look through all those sites.

> What do you want to learn ?
I need general knowledge more than anything, an overall feel of how it works. I'd prefer not to have to look up or ask how to do specific things, ideally I'd like to know the basics so when I want to do something (depending on what it is) I can work it out. For instance, the other day I had to install a new driver to get my wireless network card working on Ubuntu, I didn't know where to start, I needed someone to take me through it step by step, and I still didn't fully understand what I was doing other than that it worked, but that's no good. I like to understand what I'm doing on a computer.

I've been using Windows for 10 or so years, and I can work out how to do pretty much what I want on there. But I have wanted to give Linux a try for a long time, I've never been satisfied with Windows and I like the overall idea behind Linux, that's why I don't mind learning something new. Even though I feel like a complete beginner so far.

---

### Post by bodhi.zazen on 2007-12-18
Welcome to Ubuntu. In my experience general knowledge comes with general usage. The more you use it the more you will learn.

In the transition period most people dual boot, I know I did. This can reduce frustration of a new OS, but is also takes longer to learn an OS if you do not use it :twisted:

---

### Post by Joeb454 on 2007-12-18
bodhi's right, just use it...and post here when you have questions. *Most* people on here are friendly enough and will help. I know I'll certainly try.

Is there anything in particular you wanted to know?

---

### Post by ugm6hr on 2007-12-18
> **SegaFan said:**
>  I didn't know where to start, I needed someone to take me through it step by step, and I still didn't fully understand what I was doing other than that it worked, but that's no good. I like to understand what I'm doing on a computer.


I've been using Ubuntu for about 6 months now, having just paid a visit to these forums every now and then for a year before that.  It will all start to make sense if you just read threads here.  I find that the easiest way to learn how things work is to look at the problems & issues that other people have, and follow the advice given.  After that, google is your friend, as are all the users here.  Another useful tool for Terminal commands is:
```
man *command*
```
This will give full details about the *command*.  

The other thing to be aware is that Terminal will automatically search for executable files in the current directory and usr/bin (where most program files live in Ubuntu) if you type a *command* that doesn't exist.

As for your wifi issue...  Sounds like you were advised to manually *compile* (compiling requires *build-essential*) a program called *ndiswrapper*, which allows Linux to use Windows networking drivers.  *tar* is a type of compression (think of .zip in Windows).  The native Linux drivers were then blacklisted to prevent them conflicting with ndiswrapper by editing the *blacklist* file in *gedit* (a program like Notepad).  The Windows drivers were downloaded with *wget* (a free text-based ftp downloader).  *apt-get* is a command that allows installation of a large variety of programs in Ubuntu from the central repository (which can also be searched from *Synaptic Package Manager*).  Hope that explains how your wifi now works.  If it doesn't quite - just google all the *italicised* words, or search here.

---

### Post by SegaFan on 2007-12-19
Thanks again for all the advice.

> In the transition period most people dual boot, I know I did. This can reduce frustration of a new OS, but is also takes longer to learn an OS if you do not use it
I will install a Windows partition eventually, I need it for my work. But for now I've got everything I need for day-to-day use (internet, music, word processing, etc) up and working in Ubuntu. Is it possible to just add a partition to a hard drive or is there more to it than that?

---

### Post by bodhi.zazen on 2007-12-19
Nope, just add a partition.

You should use Gparted from a live CD (as you can not resize a partition if it is mounted, so you need to use a live CD for your root partition).

---

### Post by jan quark on 2007-12-19
Great:)

Its perhaps a little off topic but I wanted to thank for the links for the tutorials. 

Now I slowly realize that the unique Ubuntu community here in the forum is one major aspect why i completely switched to Ubuntu 3 weeks ago.

thx again and keep going

---


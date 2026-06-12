---
title: "Absolute Newb Plz Help!!!"
date: 2007-08-14
forum: Absolute Beginner Talk
---

### Post by revenge2 on 2007-08-14
Hello there, well i am a first time linux user, and i just finished installing ubuntu 7.04. And...i have no idea what im doing as i have only used windows all my life. Anyway, i have no trouble getting my way around documents etc. But i do have trouble installing.

For example i downloaded the game "CUBE" which runs on linux. I downloaded the tgz file and i dont know how to install it, so could someone please guide me as to how to do this. Oh and i was going to download the cube.win32 prior to that lol!. So as you can see i am very confused and i would like to know how to all the basic stuff.

Like installing programs, using the terminal ( reallyy need help on this badly.) etc. And setting up the internet. 

And....(sorry for all the ands btw:lolflag:)......what are all this RPM file stuf.

sigh!. 
please help through this forum...
-kind regards.:)

---

### Post by uzerzero on 2007-08-14
Your best friend for starting out is going to be the [Unofficial Ubuntu Guide]("http://www.ubuntuguide.org"). They'll have answers to almost any beginning (and advanced) issues you have. If they don't have it, chances are that a quick search will turn up any answers.

---

### Post by Hopeless on 2007-08-14
googling install software linux gave me this:

[http://www.tuxfiles.org/linuxhelp/softinstall.html](http://www.tuxfiles.org/linuxhelp/softinstall.html)

:popcorn:

---

### Post by Tux Aubrey on 2007-08-14
Ok. Downloading tar.gz files is probably not the best way to start.  Your best friend as a newbie is Add/Remove under the Applications menu.  All the installable programs there work out-of-the-box with Ubuntu without any fiddling.  

Your second-best friend is Synaptic Package Manager (Under System>Administration) - If you want the full range of software tested for Ubuntu, click Settings>Repositories and enable all except "source".  You'll be prompted to update the software list and after that you can browse or search from thousands of packages.  Its simply a matter of selecting what you want and then click "Apply".

Ubuntu is based on Debian (one of the oldest and most respected Linux distros) - it uses packages that come with a .deb extension.  Your third-best way of getting software is to find a .deb package (like an .exe installer for Windows), Download it and then double-click the icon to start the package manager application that will install it..

All the above ways handle what are called "dependencies" without you having to worry about them.

A tar.gz file is an archive (like a .zip file in Windows). It _might_ contain a .deb file but you would have to open it with "File Roller" or another archive tool.  It might be source code, in which case you will have a little bit of work (and a fair bit of learning) to do.

Another good guide to installing stuff is an article called "[How to Install Anything on Ubuntu]("http://cutlersoftware.com/ubuntuinstall/")".  

Hope this helps!

---

### Post by RomeReactor on 2007-08-14
Hi. To help you set up your internet connection, please tell us what problems are you having, if it's wired or wireless, and if you *do* have a wireless device, is it pci or usb?; also, open a terminal (Applications->Accessories->Terminal) and post the results of running the following commands:
```
lspci
```
then
```
lsusb
``` 
You won't be able to install software through Add//Remove or Synaptic until you get your internet connection going.

RPM files are what you use to install programs in Red Hat and other Linux distros that use the RedHat Package Manager; you could get them to install in Ubuntu by using a program called **alien**, but you're better off installing from Add/Remove or Synaptic, or, failing that, from DEB packages found [here]("http://www.getdeb.net/"). Maybe one of [these two games]("http://www.getdeb.net/search.php?keywords=cube") is the one you want. An easy way to install DEB files is to double-click on them.

---

### Post by proalan on 2007-08-14
Is this the game you got?

[http://ubuntusoftware.info/ubuntu_games/Action_Cube.html](http://ubuntusoftware.info/ubuntu_games/Action_Cube.html)

Looks quite decent, I might give it a go myself laters

---

### Post by revenge2 on 2007-08-14
ohk, im looking over the websites you guys gave me, i still dont quite understand....

---

### Post by jgrabham on 2007-08-14
> **revenge2 said:**
> ohk, im looking over the websites you guys gave me, i still dont quite understand....

What exactly is it you don't understand?

---

### Post by RomeReactor on 2007-08-14
Think of a DEB file as a windows EXE; you double-click it to install. [GetDeb]("http://www.getdeb.net/") is a site where you can search for programs that come in DEB format, so they're really easy to install. I would suggest that, for the moment, you don't try to install software from other sources unless absolutely necessary. First, become accustomed to Ubuntu; later you can try installing programs from the command line, or even compiling them.

For now, Add/Remove and Synaptic will be your installation friends; and you'll see they're very good friends indeed. :)

So, for now, the most important thing should be to get your internet connection working.

---

### Post by revenge2 on 2007-08-14
thanks for the site RomeReactor, yeah lol im working on the internet connection right now.

---

### Post by proalan on 2007-08-14
slow down everyone one step at a time, first he needs the internet working on his ubuntu before he can start downloading and installing packages.

---

### Post by RomeReactor on 2007-08-14
So, in order to help you set up your internet connection, we'll need to know if it's wireless; if it's wired, just plugging the LAN cable should do the trick.

---

### Post by revenge2 on 2007-08-14
its wired, but the thing is, it didnt automatically connect to the internet as i though it would after plugging in the "USB cable" ( its connected via usb). What do i do?
i cant do anything without internet, lol.

---

### Post by RomeReactor on 2007-08-14
Did you connect the usb cable just now (or recently), while the system is running? was it disconnected before? please post the output of:
```
ifconfig -a
```

---


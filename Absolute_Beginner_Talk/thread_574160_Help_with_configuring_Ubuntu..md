---
title: "Help with configuring Ubuntu."
date: 2007-10-12
forum: Absolute Beginner Talk
---

### Post by VRueLenT on 2007-10-12
Is there an application for  downloading things off the net. I mean download applications like internet download manager and others.

Is it possible to install any given windows software ( not microsoft based ) but something that belongs to Adobe and other developers  on this version of Linux ?

What is wine? How does it work, and is it free

Is there some kind of software junction from which one can download  Linux programs from

I would appreciate it if you guys would tell me why I should use this version of linux over other .iso's

Thank you! I know I asked too many questions, but then again, I got a welcome PM telling me to ask anything I would like, [ God I hope this is reasonable. lol]

---

### Post by RedMist on 2007-10-12
If you use FireFox, you can install FlashGot and then install "Downloader for X" as the download manager.

Wine is an Open Source implementation of the Windows API. Its bacically a compatibility layer between the windows code and Linux. You can visit their site here. [http://www.winehq.org/](http://www.winehq.org/)

---

### Post by bonzodog on 2007-10-12
1. There is one already installed with ubuntu. It's a little command line utility called wget. Very powerful.

Linux is not Windows. and vice versa. It is possible to use windows software using Wine, which is a 'compatibility layer' allowing windows programs to run fairly easily. We already have Adobe Acrobat Reader natively for Linux. Otherwise, try hunting for alternatives to the programs you have gotten used to. It's fun.

Wine - see above, and yes, it's free.

Most modern distro's come with what we call software repositories. This is a central server with all the software packaged and ready to go. Some 95% of commonly used applications are on the Ubuntu repositories.The Ubuntu one has 50,000+ pieces of software in it. All Ubuntu software can be installed using just one command which will fetch the software as a package, and install it for you.

Ubuntu Linux is free, it has better hardware recognition for awkward devices like wireless cards. You don't get viruses in Linux, and no spyware or freeware.

Welcome to Linux, try out the Live CD first and come back to us and let us know what you think.

---

### Post by VRueLenT on 2007-10-13
Thank you both for your helps....


As RedMist commented, I've visited the wine webpage and found the appropriate wine code for ubuntu in one of their download pages. they specified some sort of command line to paste into my terminal.

I haven't been able to download the file.. as I do not know what a sudo is or anything.

Another problem I noticed, the wget command line that was downloading some trial HTMLl pages and the speed was something in between 500 byte/s and 1241 byte/s. This is very slow but I assume it has got everything to do with my connection speed. Therefore, I need to know if there are multi-node downloading softwares for linux. Or if there are not, how could I implement those softwares working for Windows in Linux? 

I'd like a little more description about the command line, how to summon it and stuff too...

Why isn't there any virus or spyware applications in Linux anyway, is it because it is free? Is it because there is something else going on... I'm pretty sure that someone is very capable of writing some. Does it have to do with the system architecture or something?

I would like also to be familiarized with those terms.
-distro
-debian
-repositories
-APT

---

### Post by VRueLenT on 2007-10-15
Anybody?

---

### Post by mlentink on 2007-10-15
Google is your friend.
May I suggest you try to familiarize yourself a bit more with the basics of another operating system before you take the plunge. Please don't think I am patronizing, I would just like to avoid you getting disappointed

That said, a 'distro' is a version of a GNU/Linux operating system packaged for a specific purpose or with a particular viewpoint. Usually, it comes packaged with lots of application software, as does Ubuntu. Such a version is called a 'distribution', or 'distro' for short
Debian is such a distro, and Ubuntu was originally based on Debian, which is generally considered as a very stable distribution.

Repositiories are databeses of application software packages. Warehouses of software, you might say. You will usually find everything you might need in the repositories. 
The 'apt' system is the method to connect to those repositories. In Ubuntu, you will almost always connect to the repositories through graphical front-end to the apt system, such as Synaptic or the Add/Remove Software feature under your 'Applications' menu.

Please also visit help.ubuntu.com, and I strongly suggest reading the article in my signature as well.

Hope this helps a bit.

---

### Post by Baby Boy on 2007-10-15
You can use the [DownThemAll!]("https://addons.mozilla.org/en-US/firefox/addon/201") add-on for Firefox.

---

### Post by markp1989 on 2007-10-15
i have used gwget, it is just a interface for wget, and it works really well

---

### Post by twiceasworn on 2007-10-15
As a previous poster already suggested, you should really try researching some of this stuff.  There is absolutely tons of information regarding the command line in Ubuntu, as well as just about anything else.  You fortunately chose a distribution with a very avid user base who like to help.  About 8 months ago I knew nothing about Linux but I got a job as a web/network admin and had to learn.  Everything I know I have learned from the hundreds of tutorials I read on the internet.  The command line is your best friend in Linux, so it would behoove you to get intimately familiar with it.

---

### Post by VRueLenT on 2007-10-16
Once again, thank you all for your kind comments and hints that you've provided me with. They were most valuable for me.

Here is a thing I am facing right now though, I'm a Network Administrator for this small firm, I've been using windows my whole life and never even came across a Linux system before, that is in part explainable by the fact that my college discipline was far more from Computers.

The problem we are facing right now is that my firm wants to make a donation of very cheap pentium 2 and pentium 3 computers into this orphanage. and I was told that its my duty to keep the systems running. As I can't use current versions of windows with such systems, I chose to use Linux.

Now , here is the hard part. I'm supposed to give everyone an orientation as to how the system works. Plus, I'm supposed to deploy some softwares on each workstation. Those softwares are mainly written in  C/C++ and are designed for windows. But those softwares don't seem to install, and they are very, I mean very critical that we install them on those workstations.

I've been trying to install wine the past three days, but I was unable to download the 10MB file as my connection is slow (< than 12.3K). Is there any way I can download the installer files using windows and then install them here by using networking?

Plus, Ubuntu ( my current version is Feisty Fawn - Who comes up with those weird names anyway??:lolflag:) doesn't handle .exe files, as everytime I click it, it loads up this screen that says what application do I want to run this with... Need help opening that.

By the way, has anyone written a command-line list for this OS? if so, I'd like to know where I could read that.

Thanks!:)

---

### Post by BaffledMollusc on 2007-10-16
> **VRueLenT said:**
> 
The problem we are facing right now is that my firm wants to make a donation of very cheap pentium 2 and pentium 3 computers into this orphanage. and I was told that its my duty to keep the systems running. As I can't use current versions of windows with such systems, I chose to use Linux.

Okay, you might have a problem with this. It's true that Linux can run on practically any hardware out there, even really old stuff, but that's because it's extremely customizable. Ubuntu is quite a heavy Linux distribution, and is not designed to run on old hardware. I'd say it's less resource hungry than, say, Windows XP, but not necessarily that much less.

For example, Ubuntu needs at least 256MB of RAM to run properly. If your older machines don't have this you might want to look into the more lightweight version of Ubuntu called Xubuntu (see **[http://www.xubuntu.org/](http://www.xubuntu.org/)**).

> 
Now , here is the hard part. I'm supposed to give everyone an orientation as to how the system works. Plus, I'm supposed to deploy some softwares on each workstation. Those softwares are mainly written in  C/C++ and are designed for windows. But those softwares don't seem to install, and they are very, I mean very critical that we install them on those workstations.

If these C++ applications use the Windows API, you won't be able to compile them to run under Linux without using Wine. If the source code doesn't use Windows libraries you should be able to compile the apps under Linux without any problem. 

> 
I've been trying to install wine the past three days, but I was unable to download the 10MB file as my connection is slow (< than 12.3K). Is there any way I can download the installer files using windows and then install them here by using networking?

Yes, you can do this. But I'm a bit confused - the internet connection speed will be the same under Windows as under Linux. Unless you mean your Windows machine has seperate net access that is faster.

Anyway, if the computers are networked you can certainly transfer files from Windows to Linux. You can also stick the files on a USB stick and transfer them that way. The easiest way to do this would be to get the prepackaged Wine package for Ubuntu, rather than download Wine from the main Wine website. This prepackaged file should be a .deb file, which mean you can just double click on it to start the Windows equivalent of an installer.

I'm not sure where to get the Ubuntu Wine package, though. Hopefully someone else can help you.

> 
Plus, Ubuntu ( my current version is Feisty Fawn - Who comes up with those weird names anyway??:lolflag:) doesn't handle .exe files, as everytime I click it, it loads up this screen that says what application do I want to run this with... Need help opening that.

.exe files are Windows files. They don't run under Linux.

> 
By the way, has anyone written a command-line list for this OS? if so, I'd like to know where I could read that.

[http://www.linuxcommand.org/](http://www.linuxcommand.org/) is very helpful.

Hope this helps!

---

### Post by hyper_ch on 2007-10-16
First you need some basic understanding. I recommend this:

[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

then this:

[http://ubuntuguide.org/](http://ubuntuguide.org/)

As you said that should go to an orphanage have a look at this here:

[http://www.edubuntu.org/](http://www.edubuntu.org/)

Regarding your internet connectivity: I have no clue why it's transferrign so slowly. BUT by default Ubuntu comes with IPv6 enabled as primary protocoll. This means if your router/ISP doesn't support IPv6 it will take a lot longer to connect to any site (but that shouldn't be a problem once connection is established and data is being transferred). However you may want to turn IPv6 off.

---


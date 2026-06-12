---
title: "absolute beginner question: what is KDE?"
date: 2007-09-09
forum: Absolute Beginner Talk
---

### Post by willfriedwald on 2007-09-09
A few days ago I bought a PC (am a longtime Mac user) for the express purpose of running Linux & Amarok.  I installed Feisty Fawn, which I see is the familiar name for the latest edition of Ubuntu.  (I guess "Feisty Fawn" is the equivalent of Mac's "Tiger" & "Leopard.")

But there are a lot of basic Linux things that I don't understand: I have no idea what GNOME is, and, above all, what is KDE?  And what are distributions?  How do they relate to the operating system?  What do I need to know about them?

I thought that Linux was like Windows or OS X, you install it from a disc, then the system updates itself from the internet.    Would like to read more and know more about what's going on.

thanks

willfriedwald

---

### Post by zetsumei on 2007-09-09
First, welcome to linux, and Ubuntu!

Gnome and KDE are desktop environments, they interact with the kernel to lessen the amount of commands you enter to achieve tasks.  Distrobutions are different forms of Linux, for example, Ubuntu, Mandrake, Fedora and just a few distrobutions (distros for short) that come to mind.  Linux is free, so you can go to Ubuntu's website, if you wish to run Ubuntu and download an ISO and burn it to a CD/DVD and then install it on your computer.  And yes, you do update it via the internet.

I hope I answered some of your questions.

---

### Post by mikewhatever on 2007-09-09
It would take you a day or two to get used to the terminology.
[http://en.wikipedia.org/wiki/Kde](http://en.wikipedia.org/wiki/Kde)
[http://en.wikipedia.org/wiki/GNOME](http://en.wikipedia.org/wiki/GNOME)

---

### Post by Martje_001 on 2007-09-09
> **willfriedwald said:**
> I thought that Linux was like Windows or OS X, you install it from a disc, then the system updates itself from the internet.
It does. Go to System --> Administration --> update manager. Or just wait for the update icon.

---

### Post by zetsumei on 2007-09-09
Someone tell me if I was right in what I said LOL.  I haven't explained something about Linux in forever LOL.

---

### Post by init1 on 2007-09-09
KDE is a a graphical environment. It allows one to operate visually. The environment contains applications that launch programs, and move their windows, as well as the applications themselves. The environment was designed to be a standard for graphical applications, and to make Linux easier to use. Gnome is a graphical environment as well. Some prefer KDE, and others prefer Gnome. There are other graphical environments beyond these, including XFCE. Gnome has a button in the panel that allows one to update the entire system.

---

### Post by Wiebelhaus on 2007-09-09
> **zetsumei said:**
> Someone tell me if I was right in what I said LOL.  I haven't explained something about Linux in forever LOL.


righto mate.

---

### Post by rsambuca on 2007-09-09
I wasn't going to say anything,but since you asked...  The different distros are not really different "forms of linux" at all.  They are basically just different Operating Systems that use the linux kernel.

---

### Post by init1 on 2007-09-09
> **zetsumei said:**
> Someone tell me if I was right in what I said LOL.  I haven't explained something about Linux in forever LOL.
Don't worry, you know what you are talking about.

---

### Post by zetsumei on 2007-09-09
I thought I was right, just wanted to make sure.  Don't wanna be giving false info to new people LOL.

---

### Post by willfriedwald on 2007-09-09
thanks - it's sort of becoming clearer - although my desktop seems to have stuff on it that refers to both GNOME & KDE, which makes me think that both work in concert together somehow, that it isn't a case of one OR the other.

thanks - will keep reading - & hopefully master linux, my big goal being to get mySQL working in Amarok....

W

---

### Post by Happy_Man on 2007-09-09
> **zetsumei said:**
> First, welcome to linux, and Ubuntu!

Gnome and KDE are desktop environments, they interact with the kernel to lessen the amount of commands you enter to achieve tasks.  Distrobutions are different forms of Linux, for example, Ubuntu, Mandrake, Fedora and just a few distrobutions (distros for short) that come to mind.  Linux is free, so you can go to Ubuntu's website, if you wish to run Ubuntu and download an ISO and burn it to a CD/DVD and then install it on your computer.  And yes, you do update it via the internet.

I hope I answered some of your questions.
Hey there, and welcome to Ubuntu! Let's see.....

GNOME is the Desktop Environment (DE) you see when you first log in. Like, the panels, the menus, and such.Not the apps, though.  It runs on a GTK+ backend, and I believe is coded in C. GNOME is developed with the aim of adhering to the Keep It Simple, Stupid philosophy (KISS). The GNOME developers (who are different from the Ubuntu developers, btw) try to make GNOME powerful and fast while at the same time keeping it user-friendly. Programs can also be coded in the GTK+ toolkit, which guarantees that they will be coherent with the way the rest of GNOME looks. 

KDE is also a Desktop Environment. While GNOME tries to be simple, KDE has as one of its goals to put all the options it has in one place and make those options easily toggle-able. Don't let that scare you off, though. Most people only use one or two of KDE's advanced features, and they do just fine. KDE is based on the Qt toolkit, which I think is coded in C++. The Qt toolkit is almost dangerously powerful, so KDE apps are usually fully-featured, and then some. KDE also makes an effort to integrate applications. For example, you can be using the filemanager, Konqueror, and also have the ability to control Amarok (which is a native KDE app) playback and song selection, and volume, too) *from within the Konqueror window*. You can, of course, also use Amarok's window as well. Konqueror also has the ability to call other applications and open them from within itself. So, if you open a PDF, Konq will call KPDF (KDE's PDF viewer) and open the document using KPDF within the Konq window. You can also browse the internet using Konq's HTML viewer, which is integrated in the same way. There is also a package manager similar to Synaptic included in Ubuntu's version of KDE. 

Distros are nothing more than different combinations of applications and DEs packaged up together. Ubuntu is one of these. There are also others, like Debian (which Ubuntu is based on), Red Hat, Mandriva, Linspire, Arch Linux, Slackware, Gentoo, and many, many more. If you want a full list, go to [http://distrowatch.com](http://distrowatch.com).

Just one last note: In Windows (I'm not sure about Mac OS), updates from the internet are only for the OS itself, not for any other applications you install later. Not so in Linux. When updates come, they'll come for everything. You will get Firefox version updates through the update process, kernel updates, Amarok updates, every update you get (if you got it from the repositories) will come through the same update manager. That is one of the most powerful features of Ubuntu, and of LInux in general. 

I do hope this clarifies some of the confusions. Welcome to Ubuntu!

---

### Post by zetsumei on 2007-09-09
Thanks for expanding on my post Happy_Man.

---

### Post by zipperback on 2007-09-09
> **rsambuca said:**
> I wasn't going to say anything,but since you asked...  The different distros are not really different "forms of linux" at all.  They are basically just different Operating Systems that use the linux kernel.


Just to clarify this point.

There are numerous Linux distributions available.
You can look at [http://distrowatch.com](http://distrowatch.com) for a pretty comprehensive listing of the various open source operating systems. While Linux isn't the only open source operating system listed on that website, it does give a good view of what is available.

> They are basically just different Operating Systems that use the linux kernel.

Yes and No. They are all distributions of the Linux operating system using the same Linux kernel. While the kernel version may vary from distribution to distribution, in essence all Linux distributions are exactly just that. They are all Linux.

What makes them different is the view point of the distibution in regard what should and shouldn't be distributed with it. For example Ubuntu is intended to be a universal distribution of Linux which has been made very easy to install and use even for a first time user. It has an excellent repository system and provides an easy to use means of getting automatic updates to an installed system. Then there distributions such as Gentoo and Novell Suse. Gentoo provides an install method for its users which basically compiles everything for your install as you go along. It can take a VERY VERY long time (days and days possibly) to get a gentoo system up and running, however, you then have a system which has been compiled to run specifically on your hardware. Novell Suse.... Well let's just say they want to dominate the commercial business aspect of Linux, and are in bed with Microsoft and leave it at that.

Linux is Linux. But the distribution is different.

Just my opinion and thoughts on it.

:guitar:
- zipperback

---

### Post by parvinder on 2007-09-09
KDE and GNOME???????

as someone else quoted, they are different GUI environments that's all. Rest underlying OS is linux and just linux.

Some people like KDE and some like GNOME... So you may find softwares available for both environments, but you may install these programs on either GUI with/without little tweaking (I never tried but read about it)...:KS

---

### Post by willfriedwald on 2007-09-10
is there any place in NYC where I can go & take lessons in linux?  Am trying to get mySQL working in amarok and having a tough time, mainly because I have no experience with linux or terminal commands in general.

thanks!

---

### Post by adamklempner on 2007-09-10
You can find some local Linux user groups here:

[http://www.linux.org/groups/usa/newyork.html](http://www.linux.org/groups/usa/newyork.html)

Maybe there is a meeting coming up soon, or someone you can go and talk to.

---


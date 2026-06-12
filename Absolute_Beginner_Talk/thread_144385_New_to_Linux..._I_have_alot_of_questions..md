---
title: "New to Linux... I have alot of questions."
date: 2006-03-14
forum: Absolute Beginner Talk
---

### Post by ATiGuy on 2006-03-14
I have decided I am a fool for using Microsoft Windows. All I see is greed. From Microsoft's support for digitally protected content, laws being passed to close the analog gap, the copy protection technologies going into everything make me sick to my stomach. Let's not forget the hardware limitations that are going to be put into place soon to help curb piracy. I forget what the details are but I do remember that it's scary. :mad: 

It's time for me to start using Linux. I have alot of questions, this is my first time leaving the Windows enviroment and I'm scared. I installed Ubuntu without a hitch. I believe I have Dagger Drake Alpha 5 installed. I don't know how to lead into these questions, so I'm just going to ask them.

1) How did Linux start? I know some fellow invented the Unix kernel, but I don't even know what a Kernel is or does. There is a massive amount of code and complexity to an operating system. How does somebody go about building something like this? Is this all done by volunteers and hobbyists? I know there are many other versions of Linux, can somebody tell me the differences between the major ones?

2) What is RedHat and what do they do? I know this is Ubuntu, but why was RedHat charging for their version of Linux. I was under the impression that the Unix kernel is only to be used in open source or free projects or something along those lines?

3) I understand hardware support is limited in Linux. I have 2 36.7GB 10,000 RPM Western Digital Raptors (SATA) in a RAID-0 Array on my Abit NF7-S2G (NF2 Chipset). When I was installing Ubuntu, I could only see each drive individually and it was marked as SCSI. Are there any methods of having Ubuntu see the array so I can take advantage of these 2 Drives in RAID-0? I currently have Ubuntu installed on an IBM Deathstar 45.6GB 7,200RPM ATA-100. It's 6 years old and it's going to die. If I can't get Ubuntu installed to my RAID-0 array, are there issues with Ubuntu and SATA drives?

4) My resolution is limited to 1024 x 768. I assumed I needed drivers. I had an ATi Radeon 9700 Pro All in Wonder, but my PSU blew and the replacement I have can't juice it. I'm using an ATi Radeon 9200SE. I know, ATi has terrible Linux support, but I've been with ATi since 1996, never bought anything else, so I'm sticking with them. I'm a good fanboy. I downloaded the latest Linux Drivers from the ATi website. Version: 8.23.7. The file I downloaded is called "ATI Driver Installer." Beneath that on the website, I see options to download drivers for something called XFree86. I didn't download any of those. How do I go about installing this file I downloaded, is it even the right file? :-? 

5) I see all this KDE, XFree86, X.Org stuff. What is that?

That's it for now. If you could answer any of these questions, I would very much appreciate it. I will have many more questions about PHP, MySQL, and Java Development soon. I need to get the basics first though. 

Thank you!

---

### Post by Gustav on 2006-03-14
Look at this for a start :)

[http://en.wikipedia.org/wiki/Linux](http://en.wikipedia.org/wiki/Linux)

---

### Post by knalle on 2006-03-14
[QUOTE=ATiGuy]
1) How did Linux start? I know some fellow invented the Unix kernel, but I don't even know what a Kernel is or does. There is a massive amount of code and complexity to an operating system. How does somebody go about building something like this? Is this all done by volunteers and hobbyists? I know there are many other versions of Linux, can somebody tell me the differences between the major ones?
[/QUOTE]

just wanted to tell you that Linux is just the kernel written by Linus Torvalds and that its a remarkable feat but its doable for one person as Linus proved.

the rest of "Linux" that is the whole operating system and all the programs are GNU/GLP software and has been around from *NIX days, 

most of the difference between distros are their packagin system (.deb, .tgz or .rpm) and their installer/configuration.

regardless of linux disturbiution you will get the same kernel and all the same software, just configured differently

if you choose FreeBSD, NetBSD or OpenBSD you get all the same software and just a different kernel and base config

---

### Post by dvarsam on 2006-03-14
Welcome to Ubuntu!

I think for your questions 1 & 2, you could perform a "google" search for that...

In my opinion, this Forum is basically designed for solving problems regarding the USE of your Ubuntu...

It is NOT a good place to ask for info into the Linux History part...

For Linux History, take your best shot at the "Search Engines" (e.g. yahoo, google, etc.)

Take care.

P.S.> As for your other questions, I can NOT help.
I can tell you how to mount/unmount your partitions, but I do NOT know how to work on RAID (not even in Windoze)...
Resolution stuff I do NOT know...
Question 5, I have NOT experimented yet...
You are asking EXPERT stuff man.... why don't you start with the basics first...

---

### Post by AndyCooll on 2006-03-14
The link Gustav points you too is a good start.

Some quick answers:
1. See Gustav's link.
2. Red Hat are a company that distribute one of the "flavours" of Linux. Ubuntu is another flavour. Since Linux is open source anyone can take the code and modify it to suit their needs, hence why there are so many different flavours. 
3. It is not the case that Linux has limited hardware support. In fact it supports far more hardware than Winblows. The only problem is that since manufacturers usually don't release a Linux driver for their hardware then someone has to reverse engineer it. This means that sometimes Linux is behind in terms of support for the newest hardware. And yes, Linux provides RAID support.
4. Not sure about ATI, perhaps someone else can help you with this.
5. The X Window System (X or X11 for version 11, for short) is a platform independent method of providing graphics capabilities to an operating system. Gnome, KDE, XFCE are window managers which use the X capabilities to provide all graphical features you see on a GUI. With XP you are pretty much limited to the desktop environment MS provide you with, with Linux you are not. As you will find with Linux, pretty much everything is configurable to suit your own preferences and needs, and there's usually more than one choice (e.g. the different flavours of Linux). Your system can be configured to your liking (right down to compiling your own Linux OS!). It is why when people ask which is better, the usual answer is "what suits your needs the best" followed by try a few and see which you prefer (and with Linux you can do this at no cost!).

:cool:

---

### Post by Zimmer on 2006-03-14
I notice you have installed Dapper Drake, which is still in development: bear that in mind when things don't quite work, or the documentation you get pointed to does not reference it. It might have been safer to install the Breezy BAdger.
Have a read here, too, which puts some things in perspective for the Windows user tempted into Linux...
[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)
Above all, you will learn a lot through using Linux: not a bad thing.
For ATI 3D driver info please read here:
[https://wiki.ubuntu.com/BinaryDriverHowto](https://wiki.ubuntu.com/BinaryDriverHowto)

There are basically two ways of getting 3D acceleration.
The preferred way is to use the drivers provided by Ubuntu. More advanced users can also try the drivers from ati.com(this is a bit trickier for the novice) Both approaches are documented...you need take only one.
Personally, I have been using the Ubuntu provided (fglrx) and I play Enemy territory and have no issues...

There are some basic links in my signature which may help you in your journey into Ubuntu...have a good trip..

---

### Post by jobezone on 2006-03-14
[QUOTE=ATiGuy]
1) How did Linux start? I know some fellow invented the Unix kernel, but I don't even know what a Kernel is or does. There is a massive amount of code and complexity to an operating system. How does somebody go about building something like this? Is this all done by volunteers and hobbyists? I know there are many other versions of Linux, can somebody tell me the differences between the major ones?
[/quote]
Well, in unix an operating system is composed of many different parts which can be developed in paralel. Linux is just refering to the kernel, and it's not done 100% by volunteers, i.e., many of linux developers are now being paid for developing it. But, so far, they still have independece and autonomy in developing it, and it's expected by the rest of the developers that just because one gets hired by a company to develop it full time, he can't or wont dictate this companie's wishes on the direction of development. 

Eduardo

---

### Post by ATiGuy on 2006-03-14
[QUOTE=Zimmer]I notice you have installed Dapper Drake, which is still in development: bear that in mind when things don't quite work, or the documentation you get pointed to does not reference it. It might have been safer to install the Breezy BAdger.
Have a read here, too, which puts some things in perspective for the Windows user tempted into Linux...
[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)
Above all, you will learn a lot through using Linux: not a bad thing.
For ATI 3D driver info please read here:
[https://wiki.ubuntu.com/BinaryDriverHowto](https://wiki.ubuntu.com/BinaryDriverHowto)

There are basically two ways of getting 3D acceleration.
The preferred way is to use the drivers provided by Ubuntu. More advanced users can also try the drivers from ati.com(this is a bit trickier for the novice) Both approaches are documented...you need take only one.
Personally, I have been using the Ubuntu provided (fglrx) and I play Enemy territory and have no issues...

There are some basic links in my signature which may help you in your journey into Ubuntu...have a good trip..[/QUOTE]

I see where using an alpha version gets you into trouble. I need to enable universe and multiverse repositories but I don't know how to in Dagger Drake. I can't find a guide for it. :p 

Let's assume, being the resourceful guy that I am I figure out how to enable universe and multiverse repositories. Would the following text be ok to enter into the terminal? Did I modify it correctly?

Original
[i]sudo apt-get install fakeroot gcc-3.4 module-assistant build-essential debhelper
chmod +x ati-driver-installer-<version>.run
fakeroot ./ati-driver-installer-<version>.run[/i]

My modifications are in bold.

Line 1 [i]sudo apt-get install **home/tommy/atidrivers** gcc-3.4 module-assistant 
build-essential debhelper[/i]

Line 2 *chmod +x **ati-driver-installer-8.23.7-i386.run***

Line 3 ***home/tommy/atidrivers** ./**ati-driver-installer-8.23.7-i386.run***

---

### Post by ATiGuy on 2006-03-14
Thank you to everybody else who replied. The Wiki link was excellent. Hopefully over the next few years I'll become a half decent programmer and I'll become slightly knowledgeable. :p At the moment I only know high level languages and nothing else. Linux is really exciting. To think all of this is OpenSource... Wow.

---

### Post by ATiGuy on 2006-03-14
Well, I got those repositories enabled. Here's what I get... :\

[i]tommy@tommy:~$ sudo apt-get install home/tommy/atidrivers gcc-3.4 module-assistant
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package home
tommy@tommy:~$ chmod +x ati-driver-installer-8.23.7-i386.run
chmod: cannot access `ati-driver-installer-8.23.7-i386.run': No such file or directory
tommy@tommy:~$
[/i]

Any clues to what I'm doing wrong?

---

### Post by Zimmer on 2006-03-14
Not being a Dapper Drake user I am in no position to answer whether or not the route you are taking will work. 
However, you have tried to put a directory location with the install command... not required...so the install command has tried to find a package called home...
Then you have tried to chmod a file. You need to be working in the directory that the file is in to do this, or specify the full path. To go to a directory you issue the cd command... cd /home/tommy  for example.

If you were in the right place then the error means there was no file there of that name (typo? maybe , )
Hope that clears up the mystery.
As a rule the wiki instructions can be copied and pasted into the terminal, except where they contain variables  (<version>  was the variable in this particular case and you had changed it to the version number of the downloaded drivers and I assume this was correct.

Hope this helps clear up the errors mystery...

---

### Post by Bartender on 2006-03-14
If you plan on asking for help you'll be a lot better off starting over with Breezy.  Dapper's still in development.  There are many people here who will try to help with Breezy questions but aren't gonna stick their necks out trying to answer Dapper stuff because they're waiting for the official release & haven't installed it yet.      
I dumped my Radeon 9200SE for a comparable Nvidia card.  The 9200SE would lock up Ubuntu if the PC tried to run screensavers, and it would lock if I even went to the Screensavers tab.

---


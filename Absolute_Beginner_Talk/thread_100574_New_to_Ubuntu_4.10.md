---
title: "New to Ubuntu 4.10"
date: 2005-12-07
forum: Absolute Beginner Talk
---

### Post by robtygart on 2005-12-07
I got UBUNTU 4.10 from a friend and I installed it and I have no idea how to install programs off of a CD.. Such as my ATI driver for my graphic card. Or my MSN internet. 
Right now I am using my windows computer..
Both computers are home bulit.

When I insert the CD a little Disk image comes up and when I click it all it does is open the folders and files.

---

### Post by aysiu on 2005-12-07
No internet on this thing--you're limited to only what's on the CD?
For installing software, check out the second link in my sig.

---

### Post by robtygart on 2005-12-07
I was asking how to install off of a CD not off of Ubuntu..

---

### Post by cstudent on 2005-12-07
Version 4.10 was before I started with ubuntu. I started with 5.04. The current version is 5.10. You can order free cd's of it at the Ubuntu website ([www.ubuntulinux.org)](www.ubuntulinux.org)). It will take a couple of weeks to get them. 

As far as installing software, if you are able to connect your Ubuntu machine to the internet you can use Synaptic to install new programs. For me it is listed under the System menu>>Administration>>Synaptic Package Manager.

---

### Post by dickohead on 2005-12-07
I'm going to make an assumption here, you don't know a whole lot about computers right?

Which is fine, fantastic even.

So you have Ubuntu installed on your machine, and it's working correctly, you can browse the web with firefox? Listen to music etc?

One thing you might have noticed is that a lot of programs are installed for by default - ie: OpenOffice, Firefox, Evolution, Gaim etc etc

In the GNU/Linux world those Driver's disks that you get with your hardware are pretty much useless, as vendors like ATI and NVidia provide the drivers for download on the website, or some come pre-packed with Linux Distributions like Ubuntu.

Before attempting to explain why programs like MSN won't work let me just say this:

Ubuntu 4.10 - it's old now, 2 versions behind even. Get hold of 5.10 - much better.


When you are using Windows and you need to install software or drivers, generally vendors (hardware manufacturers or software writers) will provide CD's with their product. This works well for windows because it is widely accpeted as the desktop standard.

As Linux is still a new contendor for the Desktop market-place, very few vendors acknowledge it's use or importance, therefore you will not find their programs or drivers for download. But you will find many alternative versions of software, the example i'll use is MSN Messenger. Because this is a Microsoft product, it's going to be very difficult for you to get them to write a version of it for Linux, instead, we use the MSN protocl within existing message clients, like GAIM (GNU AOL Instant Messenger...i think), which can connect to Yahoo, ICQ, AIM, MSN and other networks all at the same time - muich better than one program per protocol!!!

So a short answer to your problem is:

You can't install programs like MSN on Linux, nor can you install the drivers on disks.

Why? Because they are written for WINDOWS, you need to find drivers and programs for Linux -a very good method of finding programs for Linux is to use the Synaptic Package Manager which comes with Ubuntu.

Good Luck with your travels, and may you discover a love for Linux just like many others.

---

### Post by kingsidy on 2005-12-07
4.10!!! do u mean 5.10

---

### Post by aysiu on 2005-12-07
[QUOTE=robtygart]I was asking how to install off of a CD not off of Ubuntu..[/QUOTE] Yeah, but the principle is the same. You use Synaptic Package Manager or apt-get to install packages.

The packages come either from your CD or from the internet.

In your case, especially if you don't have an internet connection on your Ubuntu installation (and you haven't said yet whether you do or not), you would have the packages come from your CD--modifying the sources.list appropriately.

---

### Post by robtygart on 2005-12-07
Well I Have built all my computers. I know my way around Windows XP, But this is  the first time I have even seen linux. 

Ok the CD I got Says Ubuntu Version 4.10 (intel x86 Edition)


I was asking how do I install a CD? I can not access the internet. I have MSN and I do not know how to install a CD..

At this time I reformated my harddrive so I can make a partition.

EDIT: Now I unerstand about the Windwos CD's

---

### Post by aysiu on 2005-12-07
Without an internet connection, installing programs is going to be painful.
Also, the installer CD doesn't have many programs on it (apart from what's already installed).

---

### Post by Qrk on 2005-12-07
Do you want to use the Ubuntu cd as a local repository? That should be set up by default, just open up synaptic with the cd in your drive. 

As to installing software from the internet, it looks like you want to download them manually, save them to a cd and then put them on Ubuntu machine? Thats also very possible. Look for packages in the .deb format, for either warty or sarge. 

[This site]("http://packages.ubuntu.com/warty/") has the warty packages available for download. Beware, though, that you'll have to get the dependencies manually, but there is a list of them at the bottom of each package page on the site. 

Once you have the pacakges, you can install them with the command

```
sudo dpkg -i *packagename*
```

You can also set up a custom repository from a CD, but this is probably easier for you.

---

### Post by funkydan2 on 2005-12-07
[QUOTE=robtygart]I have MSN and I do not know how to install a CD..[/QUOTE]

Umm by saing "I have MSN" are you asking about MSN Messenger, or is MSN your internet service provider?

---

### Post by robtygart on 2005-12-07
I Don't Have Internet For My Linux Micheen I Have Msn As My Isp. What Is Linux Good For As I Read Your Post There Is Limited Software For It..

---

### Post by aysiu on 2005-12-07
[QUOTE=robtygart]What Is Linux Good For As I Read Your Post There Is Limited Software For It..[/QUOTE] Uh... yes, **if you don't have an internet connection**. If you **do** have an internet connection, there are thousands of packages available for free that are easy to install.

I'm sorry you

1. Don't give many details about your situation
2. Don't have an internet connection for Ubuntu
3. Have a really old version of Ubuntu

---

### Post by BatsotO on 2005-12-07
If you dont have internet connection, and you using 4.10, you the package in you synaptic will be limited only to what available in the cd. That will be more simple than having internet connection using 4.10, and download some packages from internet. It's like putting xp software into win9x.  
There are some distro that ship along with many many software in the cds so you dont have to rely to much on the internet. I have suse shiped with 5 cd and mandriva with 4 cd's. Ofcourse they gonna cost you some money.

---

### Post by robtygart on 2005-12-08
Aysiu You are the most supid person I haver ever talked to I gave you all details, I can't use the software that came bundled with my Graphic crad or any other software I want FOROM A CD NOT THE INTERNT. YOUR PROGRAM SUCKS..

---

### Post by ed_d on 2005-12-08
EZ big guy, we are trying to assist.
OK, so you have version 4.10, great. You have your PC and have the cd set to boot, correct? If not, You may have to change your bios to do this, if set to boot from cd, just boot up the cd, and when it shows a propt like this:
linux#
just go ahead and hit enter. It will install just like windows does. Now, you may have to do some "tweaking" at the end of the install process, which might require you to have the internet available to you. Do you have dial up or broad band?

remember the syaing, you can catch mor flies with honey than you can with vineager....

---

### Post by Brunellus on 2005-12-08
[QUOTE=robtygart]Aysiu You are the most supid person I haver ever talked to I gave you all details, I can't use the software that came bundled with my Graphic crad or any other software I want FOROM A CD NOT THE INTERNT. YOUR PROGRAM SUCKS..[/QUOTE]
Aysiu has done a pretty thorough job of trying to explain the process to you, and you have done a pretty thorough job of abusing him for it.  


1) Linux is not Windows.
2) Programs written for one cannot be used in the other.
3) There are ways of installing equivalent programs to many of your windows programs in Linux:
   A) They can be downloaded and installed automatically over an internet connection, using tools that are already installed on the ubuntu system.
   B) Individual progams (and, more often, program components) can be obtained on removeable media, and installed manually.  These programs must either be in a binary format that Ubuntu can understand and deal with (*.deb), come as self-extracting, self-installing programs (rare), or come as source code that can be built & compiled on the local computer.

Unfortunately, most of this requires some sort of internet connection to make it run.

---

### Post by funkydan2 on 2005-12-08
robtygart - are you trying to install drivers and software that is designed for Windows on your Linux installation?  Although that seems like a really sensible thing to do, it won't work.  It's analogous to trying to put a cd onto your record player and wondering why it doesn't work.

You might get more help if you rephrased your question and asked what you wanted to achieve?  Do you need help getting connected to the internet?  If you do, then you need to give us some more details - for starters, do you use a dialup modem or some sort of cable/adsl connection?

Daniel

---

### Post by KiwiNZ on 2005-12-08
[quote=robtygart]Aysiu You are the most supid person I haver ever talked to I gave you all details, I can't use the software that came bundled with my Graphic crad or any other software I want FOROM A CD NOT THE INTERNT. YOUR PROGRAM SUCKS..[/quote]

Some friendly advice robtygart, if you want help on a forum such as this you sure as heck are not going to get it if you insult others who are trying to help you .
Ever heard of the saying , "dont bite the hand that feeds you"

Please respect other members.

Thanks

---


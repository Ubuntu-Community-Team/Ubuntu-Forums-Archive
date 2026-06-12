---
title: "Internet Connection"
date: 2005-07-14
forum: Absolute Beginner Talk
---

### Post by Deacon on 2005-07-14
I am a newbie to Ubuntu and to Linux in general.

I have Ubuntu 5.04 and am having difficulty getting Ubuntu to recognise my USB Speedtouch Broadband modem so that I can surf the net.

How do I configure Ubuntu to access the net?

Any help greatly received.

Ian

---

### Post by ign on 2005-07-14
i have a speedtouch router at home and it works fine.
is yous configured to automatically work with any computer (dhcp) or do have to configure yourself an ip address and dns?
in both cases you can access the network configuration through the system/administration menu (it's on the upper left corner).

---

### Post by odin on 2005-07-15
you should also read the ifconfig manual(man ifconfig).Dont know exactly what your problem is so if you could post a bit more of information i can try to help.I'm using ubuntu a couple of months and I probably went through some of the same problems configuring the internet conexion.

---

### Post by Deacon on 2005-07-16
[QUOTE=odin]you should also read the ifconfig manual(man ifconfig).Dont know exactly what your problem is so if you could post a bit more of information i can try to help.I'm using ubuntu a couple of months and I probably went through some of the same problems configuring the internet conexion.[/QUOTE]
 Basically, I have no idea what I am supposed to configure.  I have a Speedtouch 330 ADSL modem which I use to connect to the internet in windows via AOL.  In windows all I have to do is plug the modem in to a spare usb port, windows recognises it and then all I have to do is get the AOL software to find the modem and hey presto I'm up and running.

In Linux it seems u have to configure everything from the ground up and I have absolutely no idea how to.  I am testing a couple of Linux distros (Mandriva and Ubuntu) and am very impressed by the way most things work.  The amount of software provided is very comprehensive and everything seems to work extemely quickly and efficiently.

The only two areas holding me back from making the switch from windows are: 1. Being able to connect to the internet, and, 2. Being able to download and add new software, as rather than just double clicking on an executable file to run a setup program, I think most Linux software has to be compiled first and the somehow installed to the computer. ( I may be wrong ).

There are some help documents built into the distros, but most seem to be aimed at people with some knowledge of Linux and not the complete (never used it before and where do I start!) novice.

Please take pity on a complete newbie.

All help willingly and gratefully received.

Thanks,

Deac

---

### Post by odin on 2005-07-18
[QUOTE=Deacon]
The only two areas holding me back from making the switch from windows are: 1. Being able to connect to the internet, and, 2. Being able to download and add new software, as rather than just double clicking on an executable file to run a setup program, I think most Linux software has to be compiled first and the somehow installed to the computer. ( I may be wrong ).

[/QUOTE]


If this two are your main problems very soon you will see that you are a Linux user and forget about other OS.

You should try this:[www.ubuntuguide.org](www.ubuntuguide.org).

Almost everything you need is there and if there is any other problem you can post it here.
About your problem with the software it is actually(for me) easier than double clicking an icon to install it.
In ubuntu there's a tool called synaptics that will search in the repositories for the software you need even solving the famous dependencies.And if you want to use commands instead you can do it with "apt".Try to read in the web i told you about the repositories and also in [http://www.ubuntubackports.org/](http://www.ubuntubackports.org/) so you have a nice sources.list.Then read the manual of apt (typing in a terminal "man apt") and if after all that you still have problems post them here and I'll try to answer as soon as possible.

About your internet problems I am not sure about it so try to read at [www.ubuntuguide.org](www.ubuntuguide.org).

You should also try in [https://wiki.ubuntu.com//UbuntuHowCome](https://wiki.ubuntu.com//UbuntuHowCome)

I also had a lot of problems at the begining(I still have them  ;-) ) but when you get used to the way linux is working you will see that the time you spent was really worthy.

---

### Post by aragorn2909 on 2005-07-18
Try [this](http://linux-usb.sourceforge.net/SpeedTouch/index.html)

---


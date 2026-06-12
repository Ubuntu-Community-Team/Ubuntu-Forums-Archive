---
title: "Live CD ... Wireless network?"
date: 2007-08-15
forum: Absolute Beginner Talk
---

### Post by painreliever on 2007-08-15
I flirted with Ubuntu for a while last year and I'm thinking of now installing the latest version onto my laptop, however I want to make sure I have equivalent ways of doing all the things I do in Windows. So far I've managed to find all the programs I'm going to need so that's all good.

Now the reason I gave up before and went back to Windows was probably the same reason a lot of people do: I found it too complicated to do most things. Now I'm not a dunce with computers but I've been brought up around Windows, and as much as I acknowledge it's crappyness, I know how to use it. I was all up for Linux, I even bought a book on it from Amazon but after several weeks of getting cold-shouldered by my girlfriend for sitting up until 7am compiling kernels and finding I needed this program before I could install that program before I could install that program I decided enough was enough.

Which leads me on to my question: I bought a new laptop about 3 months ago and after being exposed to Windows Vista for this long I'm seriously considering putting Feisty on it instead. I've downloaded and burned the install CD and have been having a play with the Live CD environment. What I want to know really is; does it have ALL the features of the installed version? Specifically, does the networking work? Because I'm trying to connect to my wireless network and although my wireless adapter *seems* to be set up (I get a 'Wireless' option in the Network tab on the taskbar), I put in all the details of my network (name, password, encryption type etc) and it won't connect...

Cheers, and sorry for rambling.
Neil

---

### Post by reslider on 2007-08-15
I can't get my wireless to work in feisty either, It works awesome in edgy so maybe that could be an option if you really want to use ubuntu.

---

### Post by overdrank on 2007-08-15
> **painreliever said:**
> I flirted with Ubuntu for a while last year and I'm thinking of now installing the latest version onto my laptop, however I want to make sure I have equivalent ways of doing all the things I do in Windows. So far I've managed to find all the programs I'm going to need so that's all good.

Now the reason I gave up before and went back to Windows was probably the same reason a lot of people do: I found it too complicated to do most things. Now I'm not a dunce with computers but I've been brought up around Windows, and as much as I acknowledge it's crappyness, I know how to use it. I was all up for Linux, I even bought a book on it from Amazon but after several weeks of getting cold-shouldered by my girlfriend for sitting up until 7am compiling kernels and finding I needed this program before I could install that program before I could install that program I decided enough was enough.

Which leads me on to my question: I bought a new laptop about 3 months ago and after being exposed to Windows Vista for this long I'm seriously considering putting Feisty on it instead. I've downloaded and burned the install CD and have been having a play with the Live CD environment. What I want to know really is; does it have ALL the features of the installed version? Specifically, does the networking work? Because I'm trying to connect to my wireless network and although my wireless adapter *seems* to be set up (I get a 'Wireless' option in the Network tab on the taskbar), I put in all the details of my network (name, password, encryption type etc) and it won't connect...

Cheers, and sorry for rambling.
Neil

Hi if you can not connect through the live cd then it is likely you will need to do some work to get it working after install. If you could tell us what type of nic card it is via the command lspci in the terminal then we may can help search for a solution.

---

### Post by painreliever on 2007-08-15
> **overdrank said:**
> Hi if you can not connect through the live cd then it is likely you will need to do some work to get it working after install. If you could tell us what type of nic card it is via the command lspci in the terminal then we may can help search for a solution.

OK, I put that in and amongst other system stuff it threw up these for my WLAN and Ethernet cards:

ubuntu@ubuntu:~$ lspci
05:00.0 Network controller: Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card (rev 01)
08:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)

Cheers

---

### Post by overdrank on 2007-08-15
> **painreliever said:**
> OK, I put that in and amongst other system stuff it threw up these for my WLAN and Ethernet cards:

ubuntu@ubuntu:~$ lspci
05:00.0 Network controller: Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card (rev 01)
08:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)

Cheers

Hi and this thread has helped many
[http://ubuntuforums.org/showthread.php?t=297092&highlight=Dell+Wireless+1390+WLAN+Mini-PCI](http://ubuntuforums.org/showthread.php?t=297092&highlight=Dell+Wireless+1390+WLAN+Mini-PCI)
good luck! :)

---

### Post by LinuxLoserr on 2007-08-15
I don't really think this will answer your question but,
when you first look at the live cd, there shouldnt be any wireless network (at least thats what happened to me).
And once you install ubuntu feisty, it'll have the wireless internet up and working.
If it doesn't work out, or you're scared to try, try partitioning your drive during the installation.

---


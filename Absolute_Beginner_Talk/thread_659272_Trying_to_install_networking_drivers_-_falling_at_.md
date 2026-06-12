---
title: "Trying to install networking drivers - falling at first hurdle :("
date: 2008-01-05
forum: Absolute Beginner Talk
---

### Post by RostokMcSpoons on 2008-01-05
Hi, 

I'm trying to get my TP-Link WN321G USB wifi dongle to work in my freshly installed 7.10, and I'm having trouble following these instructions:

> I bought this device because I hadn't been able to get my Broadcom 1390 wifi device, which comes with my laptop to work under Linux. I knew that Ralink are much more open and helpful towards free driver implementations.

Unfortunately did NOT work straight out of the box. I went and downloaded the latest version of the Linux driver here: [http://rt2x00.serialmonkey.com/rt73-cvs-daily.tar.gz](http://rt2x00.serialmonkey.com/rt73-cvs-daily.tar.gz)
I downloaded them on 20070303

Unpacked everything to /usr/lib

I needed to install the kernel headers so that i could compile the driver.

in the directory /usr/lib/rt73-cvs-2007030222/Module
i used

make
make install

the module hadn't loaded by itself so i used
modprobe rt73

then configured my network settings as normal

so to recap
download the driver source from rt2x00.serialmonkey.com
unpack and go to Module directory
make
make install
modprobe rt73
configure network as per usual

The problem I'm having is that I can't create a folder in the /usr/lib directory to unpack to... is this a permissions problem?  Should I be unpacking stuff there?  I'm logging in as the primary Administrator, so I'm not sure what to try - this is, no doubt, due to my using nothing but Windows on PC's for the last 20 years, so apologies if I'm being an idiot :)

---

### Post by Happy_Man on 2008-01-05
> **RostokMcSpoons said:**
> Hi, 

I'm trying to get my TP-Link WN321G USB wifi dongle to work in my freshly installed 7.10, and I'm having trouble following these instructions:



The problem I'm having is that I can't create a folder in the /usr/lib directory to unpack to... is this a permissions problem?  Should I be unpacking stuff there?  I'm logging in as the primary Administrator, so I'm not sure what to try - this is, no doubt, due to my using nothing but Windows on PC's for the last 20 years, so apologies if I'm being an idiot :)

I believe the command is ```
sudo tar -xvcf <path to file> /usr/lib
```

Enter that into the Terminal (Applications --> Accessories --> Terminal)

---

### Post by Deadmode on 2008-01-05
:) Hey don't appologize! We are glad you are using Linux.  Lets start from the begining.  You downloaded the tar.gz file to the desktop.  Right click on it and click Extract.  It will have extracted that information to the desktop in a folder that looks something like rt73-cvs.  After you have done this you can open up a terminal window and type

user@user-desktop:~$ cd Desktop/
user@user-desktop:~/Desktop$ sudo cp -r rt73-cvs-2008010513/ /usr/lib

you can even copy and paste into terminal.  Paste by using shift insert once you are in terminal.

---

### Post by Deadmode on 2008-01-05
> **Happy_Man said:**
> I believe the command is ```
sudo tar -xvcf <path to file> /usr/lib
```

Enter that into the Terminal (Applications --> Accessories --> Terminal)

LOL your way was so much easier /cry

---

### Post by RostokMcSpoons on 2008-01-05
Thanks for the replies... as I'm shuttling between two pc's, I thought I'd try the shorter version.... but it tells me tar can't have more than one 'Acdtrux' option...?


edit:  I've made some progress using the cp method, and I've now got the driver in the right place :)   I've managed to do the 'make', and the 'make install', but the darned thing still isn't working... when I do the 'ifconfig wlan0 up' I get a message saying 'no buffer space'. I'm searching for other threads on that issue... it must be configuration because I've got 100gb of disk, and 1gb of ram.    Ho hum... no-one ever said Linux was easy, I guess :(

---


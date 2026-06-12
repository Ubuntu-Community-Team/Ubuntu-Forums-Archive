---
title: "Installation with no mouse or keyboard"
date: 2007-01-06
forum: Absolute Beginner Talk
---

### Post by dougmon on 2007-01-06
Well, here is a complete newbie post for you.

My boot from CD is extremely slow, reports errors while during the process, and ends up without mouse or keyboard support sometimes, other times ends up in a BusyBox v1.01 shell command line interface.

I will attempt to list out what the install does as I don't know the commands to log the install messages to a file (or retrieve the file, as maybe it is logging):

umcompressing Linux... Ok, booting the kernal.

[17179707l912000] hdc: timeout waiting for DMA  {I get multiple errors like this}
[17179712l916000] hdc: drive not ready for command {I get multiple errors like this}
timeout wating for DMA

Then I get: bufffer I/O error on device hdc, logical block 320359

I see from another post a user solved this problem by:

"I removed the hda line from /etc/hdparm.conf and added it to /etc/init.d/bootmisc.sh."

How do I go about making this change?

My system: 

Micron ClientPro Cn
Pentium III 933 MHz
128k RAM
Netgear WG311T Wireless Network Card
Intel 82815 Graphics Controller
Micron Keyboard and Mouse

I am attempting to run 6.06 from an ubuntu-6.06.1-desktop-i386.iso CD.  I have checked the MD5 Checkesum of my downloaded file and it is OK.  I burned the CD with Nero and verified the file afterward.

I will be running this machine with Ubuntu with more memory when I get my other PC upgrade done (Athlon X2 4200+) and will then move my old memory over to my Ubuntu machine.  If I get Ubuntu checked out my plan is to be able to dual boot my upgrade machine.

Thanks,

Doug

---

### Post by jvc26 on 2007-01-06
128k RAM? If thats the case then I'm amazed its running! If you mean 128mb RAM - then I would recommend that you try to install Xubuntu rather than Ubuntu as it is less heavy on system resources, and is designed to work on older computers. It may be so sluggish as you are low on RAM.
Il

---

### Post by dougmon on 2007-01-06
OK, 128MB.

While waiting for Xubuntu to download, I figured out how to add ide=nodma to my boot line and it has now made it without any of the dma errors clear up to a brown rectangular screen with ubuntu and an ubuntu logo on the right hand side.  It is busily reading the CD still and doesn't have mouse or keyboard support yet.  

Do you think the CD reader is having trouble reading the CD or is there some other likely problem?

BTW, the usa link for Xubuntu download doesn't seem to be up [ftp://xubuntu.d-jacobs.com/](ftp://xubuntu.d-jacobs.com/)

---

### Post by dougmon on 2007-01-07
Here is some help in case someone else experiences similar problems.  The reason that I couldn't get Xubuntu to install was that the installer itself required more than 128MB RAM, at least in my case.  So it would get part way through the install, and at the point of selecting the language (such as English), it would get very slow and the mouse button would never allow me to go to the next step.

I figured this out by transferring RAM from another PC I had.  It will install with 256KB RAM.

However, Xubuntu failed to install later on when it could not find a file.  I think it is a problem with the distribution rather than my CD, because I used a MD5 checksum tool, burned with verification, and reverified the CD.  I would report the bug as the install software requested, but at that point in time I had no way to access the new partitions.  Windows can't see them.  I could have tried to boot from a CD into Linux, but I hadn't had much success at that point.

When Xubuntu failed, I attempted to load it again, and it failed to partition correctly.  It also ruined my ability to boot back into Windows 2000.  I ran Acronis TrueImage to back up my partition (which if I was really worried about losing anything, I would have done before the initial install attempts), and used Acronis Disk Director remove the non-windows partitions to get ready for another attempt at installing Xubuntu.

I downloaded the alternate i386 version of the distribution, checked the checksum, burned a disk, and began installing.

Here is a tip for other newbies:  The text option is simply a text interface of the installer.  It is not at all that it installs a non-graphical interface version of Xubuntu!  

So the text installer is a great option on my machine because it uses less resources, installs faster, and spends a lot less time putting up fancy windows and spinning the CDROM.

By the way, I bet there are Linux tools out there that take the place of the Acronis software.  I would appreciate any advice the community has for alternatives to the Acronis.

---


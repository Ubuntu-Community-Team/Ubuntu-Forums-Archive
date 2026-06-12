---
title: "Mac os 10.5.8 ppc"
date: 2011-12-16
forum: Apple Hardware Users
---

### Post by Zenonii on 2011-12-16
I have a MAC Dual Mirrored Door G4, 1.25 GHz,  PPC OS 10.5.8 with four hd's.

I have one dedicated drive for Ubuntu.  When I first looked into Ubuntu, I was interested because it would breath new life into my non intel ppc.

I downloaded the disk image with the installer to a hard drive, then burned it to a cd.  I then tried to boot from the cd, and install, it did not.  I then attempted to use disk utility to install it from one of the other hd's.  It did not.  I booted the CD, and it installed. ...(?).

(When looking over Ubuntu, It seemed to recommended to use an older version for the ppc.  This conflicts with other literature I subsequently found).

it worked great!

But I had a couple of big jobs, and I needed photoshop, and video editing, so I used os 10.5.8.  The ONLY change I did, was add a forth hd, to use as my main boot drive.  I had to install a fresh OS 10.5.8.  No issues, and it had nothing to do with Ubuntu.

This week I went back to ubuntu, and found I have to upgrade to a newer version.  11.10.  I can find NOTHI(NG about it working with ppc architecture .  It only mentions 'intel, ' but nothing specific.

The CD I burned will NOT boot... I suppose I can try to install it from disk utility, but do I need an installer, and if so, how do I do it.

I am a solid user, but I am not a tech guy, I am new to the linux side of things.   I need help to get this mounted and in use.

Thanks in advance.

Z

---

### Post by rsavage on 2011-12-16
[https://wiki.ubuntu.com/PowerPCDownloads](https://wiki.ubuntu.com/PowerPCDownloads)

---

### Post by Zenonii on 2011-12-16
Thank you for the links.  I'm sure they will help, but how do I tell if my ppc is 64 or 32  bit?

 Z

---

### Post by rsavage on 2011-12-16
This is in the instructions. G4s are 32bit.  I didn't really follow your orginal post.  If you haven't overwritten your existing ubuntu installation then it is possible to still boot into it.

---

### Post by Zenonii on 2011-12-16
My original post is the order of events. 

I just burned two new cd's, the mini iso, and the Ubuntu 11.10 desktop.

Neither are booting.

---

### Post by rsavage on 2011-12-16
Where did you get the desktop cd from?  If it's the one from the main ubuntu site then it is not for powerpc.  The same for the mini cd - you need to choose the 32bit powerpc version.

---

### Post by Zenonii on 2011-12-17
I am stumped... I downloaded the 32 bit version, I downloaded the 'universal' installer, NEtbootin.

Netbootin has a 'line through circle' icon on the download.  I tried it four times.  It is supposed to work.  It says unsupported architecture, or there is not application to open it.  

 I have about run out of ideas.  I'm thinking there is some kind of firmware command that is saying to not recognize whatever I"m doing.  I went to a terminal, and followed the commands to the letter. When I put in a command to allow it to open and install, it said 'operation not permitted."

This is killing my time.  I 've spent hours a day trying to figure this out.

---

### Post by rsavage on 2011-12-17
Netbootin is not for powerpc.
 
I don't understand why you are having problems.  I gave you the link to the powerpc downloads.  
 
That page has a link to instructions to install.  If you want to transfer a CD to a USB device there are instructions to do that there.  I added more information about USB yesterday to make it even easier.

---

### Post by Zenonii on 2011-12-18
Savage,

I appreciate your help, but I also am not in the mood to be condescended to.  Whether you know it or not, you come off to me with a degree of arrogance.  I've spent at least 60 hours trying to figure this out, and attitude is not welcome.

For whomever may be following this:  I reset nvram, and the the cd booted instantly.  This began another slew of problems.  It said it downloaded all files, but then asked for a mirror location.  I put in a location, then it asked for a mirror host name... I searched, and found no breakdown of host name, so it said the entry was not valid.  I went to the default, in the UK, and then it said not valid host name, error message.  I went back to install and it said it could not find any disk, but it wanted to partition. ... .. ... one loop after another.  But no install.

Another sleepless night.  Anyone who wants to help, send an idea, but airs of superiority, I don't need.

---

### Post by Smithy2010 on 2011-12-18
I have an imac ppc g5 (1.8G, single-core 64 bit processor).  I had the same problems trying to boot and install 11.10, and ended up downloading merekat 10.10 for 64-bit Mac PPC.  Burned to DVD (too big for cd) and it loaded "live" fine.  When I did the install, I got a working system, but no driver for my classic airport-g wifi.  I also noticed 3 FATAL Errors during the boot up sequence.  It was looking for other PPC-64 drivers that it couldn't find them.  Looks like they have to do with internal temperature and fan control, so my fan is running very fast continuously.  This is very annoying.  I am sure there is an easy fix but I am a total newby to Linux so I have no idea where to find drivers nor what to do with them if I found them. I only know a few terminal commands.  I opened the "Additional Drivers" app thinking this was my solution.  Just got an error message and the app would't open.  I like Linux but am close to scrapping because of these issues.

---

### Post by Zenonii on 2011-12-18
I am on the run to an appointment, so this will be brief. 

I had Ubuntu running some time back, and it worked and looked great.  I found it enjoyable.  I went back to os 10, as I needed to do some involved graphics, and don't like how Gimp is set up.  it is not as well organized in its menus as Photoshop.  Photoshop, is still the best of that world.  I am thinking of doing a partition dedicated purely for video and graphics, alongside a Linux.  Also, i found a word processing app, that is very close to MS Word in it's function.  That is a good thing.  If we can get this together, it does breath new life into our older Mac architecture.

My issue is the install, not the program(s).

I am in CA, where are you?  Perhaps we can put our heads together on this.  Also, I've researched a number of others which look good, and have a distro not of Ubuntu, which is great.  I found a Linux os, that you can put on a flash drive.  it holds ALL of your active documents, the programs to run them, and the OS itself.  You can be on the road, and plug it into any computer, and have your own fully functioning familiar workstation, with your own programs, anywhere you travel.

PM  me...

Z

---

### Post by Smithy2010 on 2011-12-19
Sorry can't help with install.  Im a nubee to Linux.  My interest in Linux is that osx 10.4 is becoming increasingly obsolete.  I installed MacPorts and Porticus to take advantage of open source software and found that most of the packages require more current operating systems than 10.4.  Tried to install Dragon Nat Speaking and found it is only supported on snow leopard or later.  Too bad, the Imac is a nice machine.   Buying a new one is too much like throwing in the towel.

I am finding quite a few bugs with 10.10 and same with 11.10 when I attempted to install it.  Someone apparently moved the repositories that have many of the drivers for ppc64 architecture.  I went to the repository and found a different directory structure to the ppc64 libraries than listed on the install disk, but I don't know how to use that info to fix my system.  Let you know if I find something useful.

---

### Post by rsavage on 2011-12-20
Without wishing to sound arrogant I doubt that the above is true.

Out of curiosity what is the output of the commands
```

lsmod
lspci -k

```
please?

Btw, I suspect you have an airport extreme card, not an airport classic.  If that is the case then you need to download the firmware.  It cannot be included in Ubuntu for copyright reasons i assume, so not really a bug.  How to do download it is well documented.

---


---
title: "Need help installing on mac OS9.1"
date: 2006-11-28
forum: Absolute Beginner Talk
---

### Post by Lacent on 2006-11-28
I am new to both ubuntu and mac's, so here goes. I have an imac G3 that i am trying to put ubuntu on. It has mac os 9.1 on it right now. What i am having a problem with is getting the mac to boot from the cd. I dont know where the setting for it is. Since i am new, please speak noob. Thanks for the help

---

### Post by pay on 2006-11-28
Welcome to the forums!
I've never used a "non-pc" but you need to set the cdrom as the primary boot drive in the bios settings (I don't know how to do that on a mac).

---

### Post by tripwire on 2006-11-28
here is a good guide to help you during the installation process
[https://help.ubuntu.com/community/Installation/OldWorldMacs](https://help.ubuntu.com/community/Installation/OldWorldMacs)

---

### Post by nickburns on 2006-11-28
You may want to look into using mac's operating system software.  I don't remember what it is called, but it works just like vmware.  You boot up MacOS and then fire off another OS system, so you install Ubuntu after MacOS is up and running.  That way you can have both OS systems running at the same time.

---

### Post by 3rdalbum on 2006-11-28
3 replies, all of them incorrect. Here's the procedure from someone who's booted Ubuntu on an iMac G3.

Make sure you don't mount the disc image - that will damage it. You must burn it with Toast or a PC, using the "Disc Image" setting of your software.

The tray-loading iMac G3s have trouble reading burnt CDs. You might need to use good quality CD-Rs (the ones made for "music" work the best) or the ShipIt CDs.

Once the ISO image is burnt to CD, when you insert the disc into your Mac on OS 9, the disc's icon will appear on the desktop. When you open up the icon, it should appear with a whole bunch of folders.

Restart the Mac with the CD in, and hold down the C key. You will be taken to a black screen with white text on it - press Return, and Ubuntu will start to load.

Incidentally, how much memory does that Mac have? Ubuntu 6.06 and later require 256 megabytes of RAM, which is quite a lot for a Mac of that era to have. You can find out the memory by going to the Apple menu, then "About this Computer". The amount of RAM is shown under the heading "Built-in Memory". If you've got less than 256 megabytes, you could try Xubuntu instead.

---

### Post by Lacent on 2006-11-29
Thanks, man. That last post was just what I needed. The mac has 128mb of ram, so I guess I need Xubuntu. Is it pretty much the same procedure? I use nero on my laptop to burn my cd's, and it burns it as an iso, but when I look at it with the mac, the only file in there is the iso file. Maybe I burned it wrong? Thanks for the help.

---

### Post by Orion2014 on 2006-11-29
I couldnt have said it better myself 3rdalbum. 

Hey Corey, its Zeb. 

That is very good advice 3rdalbum has given you, pretty much exactly what I would have said. 

Gimme a holler if you have trouble installing that thing, i should be in my office for most of this afternoon.

---

### Post by Mimsy on 2006-11-29
Lacent,
If you haven't already, double-check that you burned the iso as an image, not straight up as a file. Nero has that option in one of its menus (I don't know which one, I don't use Nero, but I know it can do it). Also make sure you burn the disc as slowly as possible, to minimize the risk of reading problems when you boot from the CD.

Good luck!

/Mimsy

---

### Post by Lacent on 2006-11-29
> **Orion2014 said:**
> I couldnt have said it better myself 3rdalbum. 

Hey Corey, its Zeb. 

That is very good advice 3rdalbum has given you, pretty much exactly what I would have said. 

Gimme a holler if you have trouble installing that thing, i should be in my office for most of this afternoon.

Yeah, I was glad he gave me that advice. I got done making the Xubuntu cd and all, and I did it according to the guide 3rdalbum gave me. It recognizes Xubuntu, and starts to run it, but after the splash screen, it gives me an error message saying "Buffer I/O error on device hdb, logical block 214928"  Please help, I recorded that one on 10x the speed, and I tried a few more on 4x speed, and on the 4x, the computer just spits them out. ](*,)  I can try to do one slower, if you guys think that will help matters. Thanks for all the help!

---


---
title: "Unbuntu on Beige G3"
date: 2007-04-07
forum: Apple PPC Users
---

### Post by shan1820 on 2007-04-07
Hi,

I'm wondering what I need to do to install Ubuntu on an old beige G3. I got the computer from my work and it doesn't have an operating system installed or anything else on it. It has a cd drive which seems to work. I was reading a few things on installing Ubuntu on the beige G3 but all seemed to be based on the computer having a functioning version of OS 9 or X running on the machine. Is it still possible to get it to install from the cd without having a Mac OS? I downloaded Ubuntu Desktop 6.10 for PPC and it won't boot. I just get the disk with the question mark in it. Should I try an older version of Ubuntu? Would Dapper be better? Any help would be greatly appreciated. Thanks in advance.

---

### Post by PapaNerd on 2007-04-07
You do not need to have OSX installed in order to use Ubuntu on your G3.  In fact, it is much easier if you don't have to worry about the dual-booting stuff.  Your system admins at work may have wiped the drive clean before they let it go, so you are likely starting with an uninitialized and unpartitioned device.  Regardless of whether they did that, you may want to wipe the disk yourself before loading a new operating system, so lingering relics from the past don't surprise you at the wrong time.  My preference is the dwipe utility available from the [http://sourceforge.net/projects/disc-wipe](http://sourceforge.net/projects/disc-wipe) web page.

You should be able to boot the LiveCD by holding down the “c” key when you start the Mac.  You can then use either mac-fdisk or gparted to initialize and format the drive.  After that, just install Ubuntu (as documented elsewhere).  No need to run an older version.

---

### Post by shan1820 on 2007-04-07
Okay, all of that makes sense...the LiveCD is that just the 6.06/6.10 desktop powerpc download?

I tried that,  downloaded it on my PC and then used Alcohol 120% to burn the image to a cd. When I put that into the G3 it doesn't do anything when I press "c" on start-up. I still get the disk with the "?". Do I maybe need to burn the LiveCD on a mac instead of a PC?

---

### Post by PapaNerd on 2007-04-07
It shouldn't matter what system you used to download and burn the 6.06 or 6.10 CD ... otherwise it would be hard for anyone to upgrade to Ubuntu.  

Suggestions:
1. Do a checksum on your CD to make sure it is okay.
2. You don't just press the "c" key, you hold it down, sometimes for as long as 10 to 15 seconds (depending on the speed of the processor) until you see/head disk drive activity.  
3. Try another bootable CD in the drive to see if it works (as you could be looking at a hardware problem).

---

### Post by lcafiero on 2007-04-08
Bear in mind that a beige G3 is an Old World Mac and chances are you won't be able to boot holding down the "c" key from an Ubuntu CD. You may end up have to go the dual boot route using BootX.

There are items in another part of the Ubuntu forum -- I can't remember where I saw it -- dealing with Old World Macs and Ubuntu and how to get them to work together. I understand Ubuntu is not  officially supposed to work with Old World Macs (pity),  but it can be accomplished. It has been done by others, and they have documented their successes (but I have not been able to do it with both a G3 minitower upgraded with a Sonnet G4 card, as well as a PowerBook G3 Wallstreet).

A search of "Old World" will get you there, I think.

I'll be around because if you do have success with getting your G3 to boot and getting Ubuntu downloaded, I'd like to emulate what you do to get there.

---

### Post by Ruedin on 2007-04-08
G3 beige is unfortunately an oldworld PPC Macintosh. 
That means: You need a minimal MacOS (8.x; 9.x) & BootX. See here for more details:
[https://help.ubuntu.com/community/Installation/OldWorldMacs](https://help.ubuntu.com/community/Installation/OldWorldMacs)

About problems: See at the forum topics with one of the keyword oldworld or G3.

Sorry that I cannot help more. At the moment I can start my G3 beige with OS 8.5 and BootX, but it cannot find something (its in an other tread).

Etienne

---

### Post by PapaNerd on 2007-04-08
If you do need a legacy Mac operating system loaded on your G3, the obsolete versions can be found on the [http://www.info.apple.com/support/oldersoftwarelist.html](http://www.info.apple.com/support/oldersoftwarelist.html) web page.

---

### Post by shan1820 on 2007-04-08
Thanks everyone for all the advice and so quickly! I had read somewhere, I can't remember where, in this forum about the old world macs having a problem reading the disk if it's burned at anything higher than x2 or x4 so I'll give that a try and if it doesn't work I'll look into that link for obsolete Mac OS's and see if I can get it going that way. Thanks again for all the help and I'll keep you updated on the progress.

---

### Post by fkdev on 2007-04-08
There is also quik, if you don't want to install MacOS.
[http://www.gentoo.org/doc/en/handbook/handbook-ppc.xml?part=1&chap=10](http://www.gentoo.org/doc/en/handbook/handbook-ppc.xml?part=1&chap=10)

That being said, installing MacOS is probably a better idea.

---

### Post by stuporglue on 2007-04-08
If you're still working on booting your Beige G3, you can try these instructions. [http://stuporglue.org/oldworld.php](http://stuporglue.org/oldworld.php)

I wrote them a while back, but the procedures should be similar today.

---


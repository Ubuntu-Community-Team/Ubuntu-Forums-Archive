---
title: "3-Tiered problem: Installing, Grub, and wrong version??"
date: 2006-07-19
forum: Absolute Beginner Talk
---

### Post by blent07 on 2006-07-19
I'm as new as can be to Linux, but I've always been interested, so I thought I'd give it a try. I put in an extra 8.4 GB harddrive, formatted it, and attempted to install Ubuntu on it from the CD I made. (note: i had my dad download the ubuntu from work as we don't have highspeed out here. yes, i live in the boonies.)

First issue was in installing Ubuntu. I had the installer erase and use LVM on the slave drive i installed and let it do it's thing, since I don't know jack about partitioning. Repeatedly, the process will get to 60%, the last thing I see is Preparing xserver-xorg, then it goes to a blank screen with two small gray bars. The processor still works in spurts, but the CD-ROM ceases spinning and eventually it just all stops. Crap. 

In attempt to return to Windows on the master drive, I find that Grub, which apparently was at least partially installed, will not start. I get error 17, which I find out means it doesn't recognize the file system? The master is NTFS, i know that, so does Grub not recognize NTFS or is it something else? So basically now I can't boot anything at all. 

Finally, worry has been rising in me after checking out the installation guide at: [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
and I see that nice graphic interface that i do not have. When I boot from my Ubuntu CD, I get the option to Install in text mode or Install in OEM mode and Install a server. And when installing I get the good old blue background with white type. NOT that nice graphic setup pictured in the guide. Did my dad somehow accidentally download an older version and not the Dapper Drake? 

Sorry if I posted a too much for a single thread, but I tend to ramble. Help with even one of the problems is immeasurably apprecaited. 


Trevor

---

### Post by Klemik on 2006-07-19
Seems like he downloaded wrong CD.

[http://releases.ubuntu.com/6.06/ubuntu-6.06-desktop-i386.iso](http://releases.ubuntu.com/6.06/ubuntu-6.06-desktop-i386.iso)

This should be the correct one.

---

### Post by confused57 on 2006-07-19
Your dad downloaded the Dapper alternate CD, which is an install CD, not a Desktop Live CD(from which you can also install).  They're both Dapper6.06.
When installing in text mode, don't select LVM...probably won't make a difference configuring xserver, but you can try.

What are your computer specs, e.g. video card, CPU, memory, etc.

I'm surprised grub installed to your mbr if it didn't complete the install.
There is a way to recover the Windows mbr:
Boot up with the Windows install CD(not a recovery CD)
Select "r" for recovery mode.
Enter       fixmbr

This will reinstall the Windows mbr, effectively removing grub...

Here's a site with screenshots of the Alternate CD text install:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by blent07 on 2006-07-19
Thanks, both of you. You're right, the file even says alternate on it. I used the CD and the "recover broken system" option and it had the option in there listed to just install Grub, which I did, and that allowed me to boot into Windows. I'm having my dad download the regular version of it and bring that home to use. 

All I really know about computer, aside from that it's a Dell Dimension 4600, is that it has a Pentium 4 and 512 MB memory. I'm figuring something might be wrong with the alternate install file itself (even though it passed the "check CD" option on the CD) since it won't finish installation. I've tried both OEM and text mode with no results, but I may have skipped the text/no LVM part, which I'll try now just to see how that goes. If it doesn't succeed, then I'll just try the regular Dapper version later when my dad brings it home. 

But thanks again.

Trevor

---


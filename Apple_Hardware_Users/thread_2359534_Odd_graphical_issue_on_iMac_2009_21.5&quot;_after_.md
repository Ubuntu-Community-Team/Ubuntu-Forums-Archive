---
title: "Odd graphical issue on iMac 2009 21.5&quot; after installing Ubuntu 17.04"
date: 2017-04-25
forum: Apple Hardware Users
---

### Post by marcus2 on 2017-04-25
First post on this forum. Thanks in advance for anyone who makes it through the text and takes their time to answer.

So, I decided to try and use my old iMac 21.5" (late 2009) for something useful, to learn Linux basics and some programming. 
I went along and started to read up on how to make a dual boot with OS/x and Ubuntu on the machine using rEFInd. I started by creating a 200GB fat32 partition, to have a place to put Ubuntu, and the followed the guide on installing rEFInd (found in a stickied guide on this forum): I did a manual install, which, at least, seems to have been successful as the rEFInd boot manager starts with every computer restart. 

With rEFInd up and running I booted from the Ubuntu live cd by pressing "c" upon boot and got into the "live mode" of Ubuntu, and as all looked good i started the install.

Removed the preciously created fat32 partition, and in the free space I created a swap-partition (16GB), an EFI-partition (500MB), a bios-partition(10MB) and finally a an ext4-partition with mount point /.

Install went underway and all looked well, restarted and got back to the rEFInd boot manager. However, upon booting Ubuntu from the HD, about halfway inthe boot, something goes seriously wrong with the display... The screen splits up into four sections, all containing the same heavily distorted picture. I can see the mouse pointer, but any text is unreadable, which makes terminal a no go for trouble shooting.

Below a video showing the boot and the following graphics breakdown. Also added a pic for those not liking videos ;)
[https://vimeo.com/214621234](https://vimeo.com/214621234)

[ATTACH=CONFIG]274754[/ATTACH]

Anyone that has an idea of what is happening about halfway into the boot that makes this happen? Is it a driver issue (even though the live cd worked flawlessly)? Can I have messed up with the rEFInd installation in some way that makes the display go haywire? Any help would be appreciated.

Hardware AFAIK:
iMac 21.5" late 2009, 8GB RAM, 1GB HDD, ATI Radeon 4650, freshly installed Sierra on the OS/x side.

(Just a note: Not sitting by the actual computer until this evening so any hands on tips will not be tried until then.)

---


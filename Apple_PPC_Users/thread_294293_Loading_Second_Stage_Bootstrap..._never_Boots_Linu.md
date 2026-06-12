---
title: "Loading Second Stage Bootstrap... never Boots Linux"
date: 2006-11-06
forum: Apple PPC Users
---

### Post by amishman on 2006-11-06
I have two internal drives in my Dual 2GHz G5 Tower.  The original 160GB and a Western Digital 120GB.  For this install, I disconnected my 160GB drive as I did not want to get it screwed up <grin>  So, I just unplugged the cable, booted to my 6.10 Alternate CD, and performed the stock Install.  I had it erase the 120GB drive and install fresh Linux.  All installation went fine and it cruised along.  When it was done, it rebooted the system and I had two Yaboot options.  L for Linux or C for CD Rom.  I type the L for Linux and nothing happens and it does not boot to Linux.  I get a message loading second stage bootstrap... and it sits there forever.  I do have a small icon in the middle of the window alternating between a ? mark and a Mac face.  I left my stock 160GB drive disconnected during this time as I wanted a direct boot to Linux to tinker and when done, would shutdown and plug my main drive back in.  Anyway, install seemed to go fine.  No error messages.  I followed all the prompts.  So, why is my system not booting Linux????

Thanks

Thomas

---

### Post by hintbw on 2006-11-06
I found that I had a SCSI drive installed and it wouldn't install until I put an IDE drive in it.  Just my experience (of course I didn't have a new G5 tower, either).

---

### Post by amishman on 2006-11-06
G5 uses SATA drives.  Both of mine are SATA.

tj

---

### Post by mcruser on 2006-11-08
I'm still a newbie myself, and numerous attempts to get my G3 Ubuntu up & running have not been really successful (see also [http://ubuntuforums.org/showthread.php?t=295334](http://ubuntuforums.org/showthread.php?t=295334)). However, I did notice that at times the installation appeared successful but the system did not boot - just got the same blinking mac icon question mark trying to find an OS. It also happened at times when after unsuccessful installs I attempted reboot from CD. It seemed to be less an issue when I reinstalled the old Mac OS first, then tried reinstalling Ubuntu. I would suspect it has something to do with yaboot or difficulty finding the nonstandard OS. Just at thought.

---

### Post by amishman on 2006-11-09
Yes, I also think it is a Yaboot issue where a slight change in the text of the file will tell it where to go to get the OS but not sure how and what to do.  It is too bad not many on these forums have answers. I was hoping some Ubuntu regulars monitor these forums and offer us newbies some guidance.  I even tried going to the Ubuntu IRC channel but no one had any PPC Linux knowledge or were willing to help.  :???: tj

---

### Post by mliesenf on 2006-11-28
Ive been a long standing Gentoo and Hardened Gentoo guy. I've installed Ubuntu 6.1 x86 for some friends who wanted to try out linux. Generally, I've been very impressed because ubuntu has that clean 'just works' feel to it.

Recently I ran into a dual ppc 970 G5 system. I dropped in a WD 250G SATA drive... then I downloaded and burned 2 iso's, the gentoo ppc64 minimal .iso and also the ubuntu 6.1 ppc .iso.

The first thing I tried was the Ubuntu installation, just to see if it would 'just work'. The install process 'just worked' but after trying to reboot I was faced with this _Exact_ same problem described in this thread.

I just wanted to add my $0.02.

When I get a chance I'll use the gentoo livecd and the gentoo ppc64 install handbook to see if I can figure it out.

---

### Post by mliesenf on 2006-11-28
Alright, I figured it out.

Basically, yaboot on ubuntu didn't work.

Here's what I did.

I started it up with the gentoo ppc64 livecd.
Then I mounted the root on /mnt/gentoo.
I edited the ubuntu fstab to change the UID=### to /dev/sda ect...
Yaboot uses information in fstab to set up the bootloader.
I also edited the /etc/yaboot.conf file and included root=/dev/sda3, it didn't seem to be there in the ubuntu yaboot.conf but was on the gentoo ppc64 install page.
Then I used the gentoo yabootconfig and...
#yabootconfig -r /dev/sda3 (for example) -b /dev/sda2 -t /mnt/gentoo
Then yabootconfig does it's thing, you confirm that /dev/sda2 would be your boot... and then the computer restarts and ubuntu will load!

Fun experiment, but I'm probably gonna setup gentoo, the screen won't go larger then 1024x768, I'd like to use dm_crypted partitions, and since I'll be ploping this on the public internet... I'd like it to have some of the hardened gentoo aspects... and I think I can get dri, aiglx, and beryl running too.

---


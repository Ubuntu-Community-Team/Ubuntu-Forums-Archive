---
title: "[SOLVED] Installing Windows XP on a Ubuntu laptop"
date: 2007-08-03
forum: Absolute Beginner Talk
---

### Post by 56phil on 2007-08-03
Hi all,

I'm looking for some feedback here. :confused:

I've been happily using Ubuntu for quite a while now. Unfortunately, I must put Windows XP back on my Gateway M680 laptop. It has a 60 GB HDD and 1 GB of RAM.

I'm thinking the safest way to get this done is to backup my data, let Windows do it's own thing during installation,  reinstall Ubuntu, and finally restore my data.

The plan is to let gparted create the following partitions after the Windows install:  a 2 GB swap partition, a 8 GB shared data partition (FAT32), and a 16 GB Linux (ext3). This will leave 30 some GB for Windows and all it's bloat ware.

How does this plan sound? Is there a better way to accomplish the same task? Do have any warnings or other advice?

Thanks in advance for your help.

---

### Post by MockY on 2007-08-03
Why would you ever want a FAT32 partition?

And what's wrong with running Windows with VMware Server or VirtualBox for the few tasks (I hope/presume) you "must" have Windows for?

---

### Post by arijarot on 2007-08-03
why don't you consider to virtualize xp rather than giving it a disk partition? e.g., vmware.

---

### Post by xdarkxanarchyx on 2007-08-03
You can read/write Ext2 in windows with [EXT2 IFS]("http://www.fs-driver.org/"). It works fine, I've used it before. The only thing is, sometimes you have to reboot for it to see that you changed around the drives/partitions. That's not a problem unless you're constantly tinkering like I am :)

---

### Post by 56phil on 2007-08-03
> Why would you ever want a FAT32 partition?


Well, Ubuntu can read it too. Are you suggesting a FAT16 partition instead?

> And what's wrong with running Windows with VMware Server or VirtualBox for the few tasks (I hope/presume) you "must" have Windows for?

I didn't consider VMware because I only have a 1.8 GHz Pentium M. I thought it would be terribly slow. I need to run ArcGIS, it's not the most stable application around and it's a real resource hog. Also, I need to run Access. and I'm not sure how MS Office 2007 will take to the strange environment.

Thanks for the input.

---

### Post by splintercellguy on 2007-08-03
Have you tried using the Wine compatibility layer? Visit [http://winehq.org](http://winehq.org) to obtain latest packages. While you're at it, file a few AppDb reports :).

---

### Post by 56phil on 2007-08-03
> Have you tried using the Wine compatibility layer? Visit [http://winehq.org](http://winehq.org) to obtain latest packages. While you're at it, file a few AppDb reports

Yes, I've tried WINE. ArcGIS gets hopelessly confused. And MS Office XP won't install. Perhaps I did something wrong.

---

### Post by splintercellguy on 2007-08-03
You could try the virtualization option, you risk nothing tbh. Your plan sounds reasonable, I believe you CAN install Windows after Ubuntu, but you have to reinstall GRUB using Super GRUB.

---

### Post by 56phil on 2007-08-03
> You could try the virtualization option, you risk nothing tbh. Your plan sounds reasonable, I believe you CAN install Windows after Ubuntu, but you have to reinstall GRUB using Super GRUB.


I agree. It's just that MS installers scare the c%@p out of me. They don't play nice.

---

### Post by jackmc on 2007-08-03
for the record, you can virtualize office 07 in virtualbox :)

---

### Post by MockY on 2007-08-03
> **56phil said:**
> Well, Ubuntu can read it too. Are you suggesting a FAT16 partition instead?


Absolutely not. I do however suggest NTFS.
> **56phil said:**
> Also, I need to run Access. and I'm not sure how MS Office 2007 will take to the strange environment.

I tried both Office XP and Office 2003 via CrossOver, and it works perfectly ( don't use it though). Can only assume 2007 does the same. You could use OpenOffice Database just as well as Access. MySQL would be preferable but we are all different I guess.

---

### Post by asmoore82 on 2007-08-03
i have a 1.8GHz laptop and Windows XP is happy as a dumb little lamb running in
VirtualBox OSE on it.

it's like heaven to XP:
it has drivers for all of the "hardware" out of the box;
it always believes it's on wired ethernet card, even when Linux is actually using wifi;
it always thinks it's all alone behind a NAT firewall/router.
it can restart 20 times a day at light speed without ever even
pausing my mp3's playing in XMMS on Linux. (Once you do the 7~8 initial rounds of
updates/reboots in a Virtual Space, you never want to go back ;))

moving right along though; If you absolutely must dual-boot and are willing to rebuild
the partition layout and OS setup from scratch; I highly recommend these steps

1, boot any Live Linux CD (ubuntu/gentoo/dsl/knoppix)
2. **dd if=/dev/zero of=/dev/hda** (or /dev/sda) for just a few minutes and ctrl-c it
3. boot the WinXP install CD ... notice how it doesn't do that "press any key" routine ;)
4. create a partition for WinXp the size you want with the XP CD and install XP
5. now goto the Ubuntu install CD to make the rest of the partitions and install Ubuntu

Let XP have the first partition...
Linux is always happy to install on any partition you want;
that's a feature that I like to call "user-friendly."

---

### Post by Paulmd on 2007-08-04
> **56phil said:**
> Well, Ubuntu can read it too. Are you suggesting a FAT16 partition instead?



I didn't consider VMware because I only have a 1.8 GHz Pentium M. I thought it would be terribly slow. I need to run ArcGIS, it's not the most stable application around and it's a real resource hog. Also, I need to run Access. and I'm not sure how MS Office 2007 will take to the strange environment.

Thanks for the input.

Never mind the processor, how about the RAM? I'm running win2k In a virtual window right now on my Celeron 800mhz, Both OSes are running fine. The RAM is going to be more important than processor speed. (Win2k in updating in the background, I'm In Ubuntu typing this).  

 If the GIS program requires hardware Acceleration for video (it probably does, for 3d rendering), then you probably can't virtualize. Access shouldn't be a problem.

---


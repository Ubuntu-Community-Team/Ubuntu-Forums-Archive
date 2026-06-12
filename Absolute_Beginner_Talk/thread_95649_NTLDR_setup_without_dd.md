---
title: "NTLDR setup without dd"
date: 2005-11-27
forum: Absolute Beginner Talk
---

### Post by iand675@gmail.com on 2005-11-27
Hi, I'm having more problems.
No matter how hard I tried, GRUB always rendered both Ubuntu and XP unbootable, so I opted to install Ubunutu first, and XP second. Now NTLDR controls the boot setup and I would like to add Ubuntu to the NTLDR menu.

     Unfortunately, I can no longer boot to Ubuntu because of this, which makes it problematic for me to use the dd command to get the boot partition file. I also tried to use bootpart in windows, but can't figure out how to use it.

I have very little experience with command directories or terminals, so if anyone can help me out with this, I would greatly appreciate it.

windows is currently on F drive I think

---

### Post by amohanty on 2005-11-27
Some help can be found here:
[http://www.ubuntuforums.org/showthread.php?t=87751](http://www.ubuntuforums.org/showthread.php?t=87751)

To boot into Ubuntu you can use the live cd and then mount the boot partition to do whatever you want. 

HTH
AM

---

### Post by iand675@gmail.com on 2005-11-27
ok, well can anyone explain to me about this whole mounting thing? I've just started into linux. I've never touched linux before. Give me some idea where to start. If this terminology could be explained in further detail, that would be nice. And hoprfully some step-by-step instructions wouldn't be too much to ask for. I really am stumped at how to do this :)

---

### Post by amohanty on 2005-11-27
Hope this will clear it all up:
[http://www.tldp.org/linuxfocus/English/September2004/article349.shtml](http://www.tldp.org/linuxfocus/English/September2004/article349.shtml)

HTH
AM

---

### Post by iand675@gmail.com on 2005-11-27
okay, um but how do I use the dd command and how do i know what hard drive to mount?

---

### Post by amohanty on 2005-11-27
the dd command has the following basic syntax

dd if=<input file> of=<output file> bs=<block size> count=<number of blocks to copy>

to copy the entire file just do a :
dd if=<input file> of=<output file>

To find out which drives are mounted just do:
fdisk -l

or
 
df


HTH
AM

---


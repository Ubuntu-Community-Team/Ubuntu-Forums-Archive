---
title: "Ubuntu hangs on start up before going to Busybox command prompt with odd messages"
date: 2007-11-25
forum: Absolute Beginner Talk
---

### Post by Ruanae on 2007-11-25
Hi

Been searching the forum and can't really find anything similar to this so am posting this in the hope someone may be able to help. Or point me in the right direction.

I installed ubuntu 7.10 on my old computer the other day (1.5GHZ Amd processor, 512MB ram, 256mb Radeon, um something card (Can't remember exactly sorry)) and it was working fine. I ran the upgrade program to get all the updates and they seemed to be installed without a problem. 

I've just gone to boot the box now and it gets as far as the loading progress bar, which doesnt move for a few moments and then i get the BusyBox command prompt on screen. On the command prompt screen I get messages such as: 
[ 1012466106] ara1.: exception Emask 0x0 SAct x0SErr 0x0 action 0x2 frozen
or 
I/O Exception on device sda:logical block 0 
or 
ldm_validate_partition_table():disk read failed.

I thinking that something on my hard disk has failed, but was posting on here first to either check if anyones come across anything like this before, or if anyone could suggest a solution, other that replace the hard disk.

Thanks for your time

---

### Post by popch on 2007-11-25
It looks like you disk drive failed. At least two of the three error message you cite seem to be saying that.

I would suggest that you boot your PC from the liveCD with which you installed Linux on your PC, and running off the live CD try and recover the contents of your disk.

---

### Post by Ruanae on 2007-11-26
Hey thanks for your response. I will try that when I get a moment. Do you happen to know the best way of recovering information off the drive? Is there a tutorial for doing so in ubuntu?

Thanks again

---

### Post by popch on 2007-11-26
I have as yet never needed to recover a damaged drive or partition. Also, my experience in backing up damaged partitions is not such that I could recommend a safe course of action. Best have a look at the help system and the wikis on Ubuntu's web site.

Perhaps some of the more experienced members here can give you a bit of guidance.

One piece of advice I can give: Do back up your disk and make doubly sure that you really have a usable backup before trying to change anything at all on your disk when you attempt to recover your data.

---


---
title: "Dual boot with XP and Ubuntu"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by Thorun on 2007-06-24
Hi. 

I have been running Ubuntu v7.04 for some weeks in a dual boot with WinXP. It works like a charm..... most of it...

Now i know a little about GRUB and how it's installed on the first partition - nomatter what OS there is on that partition. 
Now i want to make things easy for myself e.g. making partitions enough to play with several different linux-distros. Hence - I will try to make my installations in such a way, that i can use partimage on different partitions that don't destroy GRUB

My idea is to (i have a dell laptop where there is a 72mb fat16 partition at the wery beginning of the HD) make room for several linux distros that can use the same SWAP-partition. And i allso want the different distros to have the same /home folder (on another partition). On my primary linux distro (ubuntu) i will install several Virtual Machines eg. Win98, WinXP, and others.

That i would like to make - in a dual boot with Windows XP. 
I would like it to be as bullet proof as possible. I use (in windows) Northon Ghost a lot because i play with my Windows a lot. And in Linux i use partimage a lot because that gives me the freedom to play a lot on my new OS too.

My question is: How can i make this happen in the most safe way?


My plan is to partition my 60GB harddrive to:

1: Primary partition: fat16 - the default Dell partition
2: Primary partition: Ext3 - my main Linux - Ubuntu
3: Extended partition: Ext3 - Linux OS no. 2
4: Extended partition: Ext3 - Linux OS no. 3
5: Extended partition: SWAP
6: Extended partition: Ext3 /home  (for all 3 Linux distros)
7: Extended partition: NTFS - Windows XP
8: Extended partition: NTFS - shared partition with music and stuff.


Is this possible?
Is there something i could do to make it more "bulletproof" ?
Is it possible to (if failure some day) to re-install windows XP on partition 7 without messing up GRUB?

Regards Rune
/Denmark

---

### Post by ubu-for on 2007-06-24
Try [this](http://ubuntuforums.org/showthread.php?t=482051&highlight=grub).

---

### Post by Thorun on 2007-06-24
@ubu-for

I have read the post you linked to, but that didn't give me much of the answers i was looking for...
The last post just confirmed me in, that i have to be carefull and seek advice before starting with my project.

---

### Post by ubu-for on 2007-06-24
First of all, you have to install Windows before you install any Linux distributions!

And second, I don't think that you can use one SWAP and home partition for all three distributions.

---

### Post by louieb on 2007-06-24
Bullet proof and a shared /home partition do not go together. Different flavors of Linux do things, well differently.  Could run into trouble running different versions of the same program.  What I did  was create a data partition for stuff I wanted to share between OSes.
>  Now i know a little about GRUB and how it's installed on the first partition - nomatter what OS there is on that partition. **Not true**. There are two parts to GRUB the GRUB program itself is usually found in /boot/grub/stage2.  The other part is a pointer to the GRUB program.  Most Linux distros give you the option of putting it in the MBR of the hard drive or in the boot sector of any partition.  
>  7: Extended partition: NTFS - Windows XPHaven't tried putting XP on an extended partition but I've read that its a pain to do. 
>  5: Extended partition: SWAP Works like a charm.
 > ..make things easy ... play with several distros .. don't destroy GRUBLook at chain loading or using a configfile. Both will help keep you distros safe when it come to kernel update time. For more info     [Illustrated Dual Boot Site]("http://users.bigpond.net.au/hermanzone/")
;)Linux is fun to play with and for real work its what I use too.

---

### Post by Thorun on 2007-06-24
Thank you for the replys - and for the link the the illustrated dual boot site.

Now i have read somewhere, that it's a good idea to make a /boot partition at the wery beginning of the harddrive. I don't know why do to that, but it sounds like a good idea.

---

### Post by louieb on 2007-06-24
> **Thorun said:**
> Now i have read somewhere, that it's a good idea to make a /boot partition at the wery beginning of the harddrive.
The reason for the /boot partition is some machines with older BIOS cannot boot a program unless it is within 1000 cylinders from the start of the hard drive. 
IMHO: Unless the BIOS on your PC has this problem, using a separate partition for /boot is more trouble than its worth.

---

### Post by Thorun on 2007-06-24
@Louieb. 

Ok. Thankyou for the info on the /boot partition. I've decided not to make that partition - as my computer is a allmost new Dell laptop... Shouldn't cause any problems :D

I'm still reading the link you gave me. There's loads of pages with info that's good to know.

---


---
title: "[SOLVED] partition question"
date: 2007-12-02
forum: Absolute Beginner Talk
---

### Post by alphaniner on 2007-12-02
Yes, another partition question.  A thousand apologies, but I couldn't find an answer to my question anywhere on the forums or the docs after about 30 mins of searching.

The Story So Far...

I just did a clean install of windoze and left a nice chunk of disk unpartitioned.  Ubuntu (7.10) has loaded from the live CD and I am going through the install process started from the icon on the desktop.  And as you may have gathered I'm at the point where I have to set up my partitions.  As far as I can tell, the only way I can use the unpartitioned space is to use the 'manual' option so I am looking at the 'Prepare Partitions' screen.  I select my free space, click the 'New partition' button, and the "Create partition' dialog pops up.  My intention is to create two partitions: one for the OS and one for swap.  Everything is straightforward except the option "Type for the new partition: Primary/Logical."  What is the difference between the two, and which should I use?  Thanks.

---

### Post by PeterJS on 2007-12-02
> **alphaniner said:**
>   What is the difference between the two, and which should I use?  Thanks.

The way hard disks are set up is that they can only have 4 primary partitions, and you can only boot from a primary partition. A logical partition is a sub partition of a primary partition to get around the limit of 4 primary partitions per disk. If you're planning on using 4 or less partitions there's no reason to use a logical partition.

---

### Post by alphaniner on 2007-12-03
> **PeterJS said:**
> The way hard disks are set up is that they can only have 4 primary partitions, and you can only boot from a primary partition. A logical partition is a sub partition of a primary partition to get around the limit of 4 primary partitions per disk. If you're planning on using 4 or less partitions there's no reason to use a logical partition.
Brilliant! I couldn't have hoped for a better answer.  You, sir, are a gentleman and a scholar.

---

### Post by nae5 on 2007-12-03
think ima steal that sig.. :)

---

### Post by Paqman on 2007-12-03
> **alphaniner said:**
> My intention is to create two partitions: one for the OS and one for swap.  

Have you considered including a seperate /home partition? It makes reinstalling (almost) completely painless.

---

### Post by alphaniner on 2007-12-03
So I made my two partitions as primary and went along with the install.  Everything seemed to go fine, but then when the computer rebooted it went straight to windows (XP SP2), no bootloader or anything.  I got the impression from the docs that the GRUB bootloader is supposed to initialize by default, am I mistaken?  Also, I don't know if it matters but I have one PATA HDD and one SATA HDD, and the SATA HDD is my boot drive.

---

### Post by alphaniner on 2007-12-03
> **Paqman said:**
> Have you considered including a seperate /home partition? It makes reinstalling (almost) completely painless.
I read about the benefits and I may end up going that route eventually, but I'm just not a big fan of breaking up my disk any more than I have to.  I haven't partitioned a HDD since the days of Win 9x.

Plus, I'll likely screw things up so spectacularly the first few times that I'll *want* a complete reinstall :)

---

### Post by alphaniner on 2007-12-03
I ran the Super GRUB Disc and that installed the bootloader.  However, for some reason it decided my partition is on (hdd 1,1) when in fact it is on (hdd 0,1).  I can use GRUB to edit the line and boot Ubuntu, but apparently the edit is not permanent and I have to do it every time I want to start Ubuntu.  How do I make the change permanent?  Thanks.

---

### Post by lamalex on 2007-12-03
to make the change stick, edit /boot/grub/menu.lst

---

### Post by alphaniner on 2007-12-03
Thanks, that did the trick.

---


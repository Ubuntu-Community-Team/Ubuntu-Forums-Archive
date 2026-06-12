---
title: "Trouble getting XP install alongside Gutsy"
date: 2007-10-16
forum: Absolute Beginner Talk
---

### Post by RedGreen on 2007-10-16
I have Gutsy installed in a partition and now I am trying to install XP on a different partition to dual boot. I was having trouble getting the install to recognize my hard disc, after changing the SATA setting on this laptop to compatibility. that resolved that issue. When I load up an XP pro disc it only sees an unknown partition (the one my linux install is on I think) but even when I use gparted to create an ntfs partition and that was not recognised.

I tried putting a vista disc in and booting up, it saw all the partitions on my HDD and was even able to create a partition with it but every time I click next it says the criteria hasn't been met for the install.

Any suggestions will be greatly appreciated. Let me know if you want any info I left out.

---

### Post by 001100 on 2007-10-16
did u ever have xp installed installed on it b4??? It might not have the corrent hdd drivers?

---

### Post by reza81 on 2007-10-16
With your method of installation. you should install XP first

---

### Post by 001100 on 2007-10-16
Yes reza81 is right you should have going with installing xp first. But stil you should make sure you have the right hdd drivers for the xp instllation.

---

### Post by RedGreen on 2007-10-16
> **001100 said:**
> did u ever have xp installed installed on it b4??? It might not have the corrent hdd drivers?

I am using a Thinkpad Laptop, It came with Vista pre-installed and I burned recovery discs and installed Gutsy over that space.
> **reza81 said:**
> With your method of installation. you should install XP first
I understand that that would solve some problems, although I really do not want to start over after getting so much working in Gutsy on this computer. So if any idea on how to solve my current situation while leaving my Gutsy partition intact?

---

### Post by RedGreen on 2007-10-16
> **001100 said:**
> Yes reza81 is right you should have going with installing xp first. But stil you should make sure you have the right hdd drivers for the xp instllation.

I am a little confused. What HDD drivers? I have never had to deal with drivers to just install an OS before. My desktop is using a SATA (seagate even the same brand) drive and diddnt have any issue with drivers for being able to install.

I am not finding much on the seagate site about drivers, just various programs.

oops sorry about the double post

---

### Post by victorgreen on 2007-10-16
Ive installed 7.04 on a similar laptop and then made a partition and put visturd on it. It worked no problem. I pre formatted the partition in gparted with ntfs.

---

### Post by iansane on 2007-10-16
That thing about HDD drivers is confusing to me to. How can you install drivers if you don;t have an OS installed? I'm a noobie so I don't understand everything so if I'm missing something, sorry. I would like to know how to set up the dual boot after Ubuntu is allredy installed too. I did install XP first. That way is easy though cause the live CD takes care of everything. It seems like it would have something to do with using 3rd party software to resise and create the NTFS partitiion and then some rewriting of the GRUB boot loader to make it work. Is there a step by step tutorial on this subject? Maybe somewhere in some dual boot tutorials?

---


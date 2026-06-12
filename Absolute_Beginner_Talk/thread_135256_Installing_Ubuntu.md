---
title: "Installing Ubuntu"
date: 2006-02-23
forum: Absolute Beginner Talk
---

### Post by merlined on 2006-02-23
Hello there,

I am completely ignorant to linux and its operating systems and I have a couple of questions before I install Ubuntu.

If I install Ubuntu will I lose any files, such as my writings, my songs and other things of that nature? Should I create a back up for all of that? I have two hard drives, if I install ubuntu will it wipe out anything on my second hard drive? Or will it even recongize my other drive?

Also, to make the transition easyer from windows to ubuntu I would like to have the option to load up in windows or in ubuntu if that is possible. I believe this would have something to do with partitoning the drive and such, and I don't know how to do this, though I have heard that some linux operating systems ask you to if you want to partition when you install.

I would like to have access to all of my files that are saved in my windows places. So if I load up in Ubuntu will I be able to use and modify all of my pictures, songs, videos, and documents that have already been saved? I know I would need an equivilant application to open these things in Ubuntu, but I would like to know if I need to do more to play around with the files that are already saved on my windows computer. 

Thank you very much for this forum, I am sure this will help. By the way the main reason why I am making the switch is because of the meaning of the name "Ubuntu" and the idea of sharing to better the whole. The idea that we are all here on earth together, and the more we work with each other and the earth the better off we will be individually is an idea I think will eventually grow from organizations like this and into the policies that affect billions around the world. Keep up the good work!

Kris

---

### Post by knalle on 2006-02-23
[QUOTE=merlined]Hello there,

I am completely ignorant to linux and its operating systems and I have a couple of questions before I install Ubuntu.

If I install Ubuntu will I lose any files, such as my writings, my songs and other things of that nature? Should I create a back up for all of that? I have two hard drives, if I install ubuntu will it wipe out anything on my second hard drive? Or will it even recongize my other drive?
[/QUOTE]

Done right you will not lose your files and you can "dual boot" between Windows and Linux easily.

First of all make sure you understand harddisk **partitions** or buy a separate hd for ubuntu.

When you run the installatin of ubuntu it will ask you if you want to install **GRUB** and that takes care of boot both windows and ubuntu.

To access your windows files make sure they are on a **fat32** partition, this is the only safe way to use windowsfiles from linux yet.

Happy Hacking

---

### Post by Klaidas on 2006-02-23
[QUOTE=merlined]If I install Ubuntu will I lose any files, such as my writings, my songs and other things of that nature? Should I create a back up for all of that?
[/QUOTE]

Everything should work out and our files should be safe, but it's always better to make a backup of all the data before installing linux.

> Also, to make the transition easyer from windows to ubuntu I would like to have the option to load up in windows or in ubuntu if that is possible. I believe this would have something to do with partitoning the drive and such, and I don't know how to do this, though I have heard that some linux operating systems ask you to if you want to partition when you install.

Yes, you can. You should set up dual booting. Check this guide: [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

> I would like to have access to all of my files that are saved in my windows places. So if I load up in Ubuntu will I be able to use and modify all of my pictures, songs, videos, and documents that have already been saved? I know I would need an equivilant application to open these things in Ubuntu, but I would like to know if I need to do more to play around with the files that are already saved on my windows computer. 

This depends on you file system. If it's NTFS, it will be read-only. Otherwise, as I know it will be possible 

PS: Welcome to ubuntu! ;)

---

### Post by jjf on 2006-02-23
[QUOTE=merlined]
If I install Ubuntu will I lose any files, such as my writings, my songs and other things of that nature? Should I create a back up for all of that?[/quote]

I'll second what Klaidas said: your data should be fine, but back up anyway just to be safe.

> I have two hard drives, if I install ubuntu will it wipe out anything on my second hard drive? Or will it even recongize my other drive?

You have many options for installing Ubuntu.  One of them is to wipe your second drive clean and put Ubuntu on it, but you don't need to do it that way.  If you want to preserve your data:

1. Defrag your hard drives in Windows (IMPORTANT!)
2. Get a Linux Live CD with a partition manager (I like [SimplyMepis]("http://www.mepis.org/node/1462")) and use it to shrink your Windows partitions.  Leave the extra space unformated.
3. Get a Ubuntu CD, and install into the unformated space.

If this sounds technical and complicated, please ask and the very friendly folks here can step you through these.

> Also, to make the transition easyer from windows to ubuntu I would like to have the option to load up in windows or in ubuntu if that is possible. 

This is possible, and not hard with Ubuntu.  During installation, Ubuntu will detect that you already have Windows installed and ask about configuring GRUB to dual boot.  Say "yes" and you should be set.  (It works like this: during boot-up, you'll see a message on your screen that says "Press ESC to enter the GRUB menu."  If you press escape, you can choose whether to boot into Windows or Ubuntu.  If you don't press escape, after 10 seconds it automatically boots into the default OS.  The default OS starts out as Ubuntu, but you can change it to Windows.)

> I would like to have access to all of my files that are saved in my windows places. So if I load up in Ubuntu will I be able to use and modify all of my pictures, songs, videos, and documents that have already been saved? I know I would need an equivilant application to open these things in Ubuntu, but I would like to know if I need to do more to play around with the files that are already saved on my windows computer. 

Short answer: In any case, you will be able to READ files from your Windows partition in Ubuntu.  But if you have Windows XP, you probably cannot WRITE files back onto your Windows partition.  The reason for this is that Windows supports two different formats: FAT32 and NTFS.  Linux can read both formats, but can only write to FAT32.  Windows XP by default formats the drive as NTFS.

One work-around is to make an extra partition, format it as FAT32, and use it to swap files back and forth from Windows to Ubuntu.

Welcome, and good luck!  :)

---

### Post by merlined on 2006-02-23
Thank you all for replying. When I get home I am going to try these things and get started!

:)

---

### Post by adrenaline on 2006-02-23
First of all, there is some great advice in this post!

I recently dual-booted my laptop with xp home on it about a week ago and it was surprisingly simple!  The only suggestion I have to add is to use a Live CD of GParted instead of downloading SimplyMepis.  Although both will get the job done, GParted itself is only about a 35MB download as opposed to the 600+MB download of SimplyMepis.  

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

Just go to the download page and click the "gparted-livecd-0.2.iso" link.

Good luck! :)

---


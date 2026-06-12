---
title: "Simple Backup - items to backup to be SAFE"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by Tony3286 on 2007-10-20
With Gutsy ready to download, I wanted to make sure, BEFORE upgrading, that I have all
the important files backed up. I have installed Simple Backup - the default folders listed are:
/var   /home/   /usr/local   and    /etc/  .  I use Gnucash and have that info backed up separately.

My main question is , are there other data files that should be backed up? I have for example a program called "Car" that is a program to keep track of my car maintenance. I'm new to Linux, and I'm not sure where these type of programs save your information. Do I have to save the entire folder and include that with the "Simple Backup" or do these type of programs save to a common folder thats listed above ?  One other question - would the default directories above
contain all my preferences that I have in Feisty.

I'm sorry if these are simple minded questions but I love Ubuntu, have got it just the way I want it and want to make sure my preferences and data are backed up correctly.

---

### Post by Paqman on 2007-10-20
All your software preferences are stored in your /home. They're hidden by default. If you go to /home/yourusername in Nautilus and hit Ctrl-H you can see them all (the ones like .foldername )

---

### Post by Irony on 2007-10-20
This is the simplest way of backing up your entire system;

[http://ubuntuforums.org/showthread.php?t=416710](http://ubuntuforums.org/showthread.php?t=416710)

It is literally copying your system into another separate drive (or partition) - if you need to restore it, simply copy it back. There is no compression involved as it is literally a copy.

---

### Post by kerry_s on 2007-10-20
dude why even bothering trying right now, don't you see all the complaints about gutsy? you should give it a little time, let them upload some fixes.

nice that you backed up though, from the sound of things, your going to need it. :(

---

### Post by Tony3286 on 2007-10-20
I'm definitely waiting a MONTH after reading all the problem posted for Gutsy upgrade. I presently use  a Western Digital external hard drive formatted with FAT 32. If I do the full copy  to that drive will the FAT 32 format cause a problem if I then copy that backup back to my Linux partition if i needed too?

---

### Post by kerry_s on 2007-10-20
> **Tony3286 said:**
> I'm definitely waiting a MONTH after reading all the problem posted for Gutsy upgrade. I presently use  a Western Digital external hard drive formatted with FAT 32. If I do the full copy  to that drive will the FAT 32 format cause a problem if I then copy that backup back to my Linux partition if i needed too?

i'm not sure, but i don't think fat32 preserves permissions, so you might have some issues there. you should probably use a linux fs to back up a linux system.

---

### Post by mikeyphi on 2007-10-20
OR you could download 'partimage' and save the entire partition - then play as much as you want!!

---

### Post by Tony3286 on 2007-10-20
OK I downloaded Partimage - I went into terminal typed Sudo Partimage - and chose my linux partition, but when I try to save - it tells me it can't  copy because the linux partition is mounted.
How can I start Partimage  AND not be in Ubuntu

---

### Post by mikeyphi on 2007-10-20
Sorry about that!!

Look here for a LiveCD: [http://www.partimage.org/Main_Page](http://www.partimage.org/Main_Page)

---


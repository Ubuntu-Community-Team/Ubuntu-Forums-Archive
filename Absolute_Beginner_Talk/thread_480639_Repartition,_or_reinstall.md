---
title: "Repartition, or reinstall?"
date: 2007-06-21
forum: Absolute Beginner Talk
---

### Post by stingerssx on 2007-06-21
I thought that this would be a good place for this.

   I have 6.10 (Edgy), and I am starting the complete migration to Linux. I installed it to a HDD for my main computer, (120 gig). The original was a 60 gig (NTFS Windows XP). I tried to partition the 120 gig drive to 60 gigs for Ubuntu (and then I would have cloned the current NTFS 60 gig to the remaining partition) when I was installing it, but it would just hang. The only way that I could install 6.10 was to full erase and install.  Since installing, I have upgraded to 7.04 (Feisty). 

   I'm wondering if I should download Feisty, and reinstall Ubuntu with the 60 gig partition, or if I should keep the current installation, and repartition it. I have read heard, and experienced that Windows doesn't like to let other OSes be installed. So Linux needs to be first, then Windows should be installed. I don't really know how to manually partition the drive, but that I could learn. Would that be better?



   Thanks in advance.

---

### Post by Skrynesaver on 2007-06-21
Actually it's the other way around, Windows will not let you boot another OS so partition first, then install windows on one partition then install Ubuntu 

If you're starting from scratch, then just follow the menus on the live CD you'll find it easy enough

---

### Post by stingerssx on 2007-06-21
Ok, so you're saying to initially partition the (120 gig) drive into two equal  60 gig partitions, (for example) then to install Windows on one partition, and then install Ubuntu on the other? What program, or OS do I use to partition a blank drive? Windows XP will let me when installing, right? (I don't remember). Then install Ubuntu on the remaining 60 gig partition? 

     Oh yeah, I don't want to do a clean install of Windows, I want to clone my existing 60 gig Windows drive. How could I go about this? I think I have Norton Ghost, Maxtor Max Blast, and a Sea Gate program, and another one from Western Digital. They came with the new drives.

   I really haven't gotten too far into Ubuntu, and the mass of my files are on other NTFS formatted drives, so I could wipe this (120 gig) drive clean.

  Like I said, I have the majority of my files on other HDDs, so I would only need 60 gigs to clone to, and I could use the other for Ubuntu.
   I'll start downloading 7.04, Feisty Fawn.

---

### Post by Hobo Joe on 2007-06-21
When you install Windows, just do it like you normally would.(Whole disk)
Then when you isntall Ubuntu, just resize the Windows partition to 60 GB(or whatever it is that you want) then make a ext3 partition and a swap partition.(I'm assuming you know how to do this, considering that you've installed Ubuntu before.)

---

### Post by ookadoo on 2007-06-21
You should check out ghost 4 unix (g4u):

[http://www.feyrer.de/g4u/](http://www.feyrer.de/g4u/)

It is console based.  I have had troubles that you described (hanging) when trying to use qtparted or gparted in ubuntu's live cd mode.  g4u is very powerful and tiny.  You could even put it on a USB drive though I haven't done that, just a cdrw.

---


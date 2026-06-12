---
title: "Please help windows can't see drive"
date: 2007-01-12
forum: Absolute Beginner Talk
---

### Post by Guy Smiley on 2007-01-12
Hi somebody please help.
I've got a dual boot machine. I carried out a reinstall of Ubuntu, and it now works fine, but window has 'lost' one of the nfts drives. its on the desktop in ubuntu so i know its still there. do i have to amend the grub to get windows to recognise it again ?

---

### Post by MetalMusicAddict on 2007-01-12
Is this a separate drive from the OS? A storage drive?

---

### Post by rccharles on 2007-01-12
> **Guy Smiley said:**
> Hi somebody please help.
I've got a dual boot machine. I carried out a reinstall of Ubuntu, and it now works fine, but window has 'lost' one of the nfts drives. its on the desktop in ubuntu so i know its still there. do i have to amend the grub to get windows to recognise it again ?

I would suggest you backup the data on this drive from Ubuntu.

In Ubuntu, do:

Applications > Accessories > terminal

enter the command:
sudo fdisk -l


the command below will create a file please post the results here.

sudo fdisk -l >fdiskout.txt


...

Windows requires the correct ID.  Maybe you could try the Windows check disk command.

Robert

---

### Post by Guy Smiley on 2007-01-13
Robert that last comment sorted it thankyou i really appreciate your help.
Basically I rebooted into XP, went to Computer Management (from Control Panel / Admin Tools) and selected disk management. The NTFS drive was there (shown as 'healthy') and all I needed to do was to assign it a drive letter.

---


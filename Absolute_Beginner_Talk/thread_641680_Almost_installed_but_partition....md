---
title: "Almost installed but partition..."
date: 2007-12-15
forum: Absolute Beginner Talk
---

### Post by The Linguist on 2007-12-15
I just ran the latest live CD and went through the install wizard but backed out at the last second. It seemed to me that it was going to overwrite my XP install. I couldn't figure out which option created a new partition for ubuntu without touching the current XP install.

---

### Post by jken146 on 2007-12-15
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing) is a good beginner's guide to installing Ubuntu.  Basically, though, to preserve your Windows install, don't choose the option "Use entire disk".  A backup of your important files might be a good idea if you're not sure what you're doing.

---

### Post by The Linguist on 2007-12-15
I looked at that, but the slider bar option for running a dual boot was not an option. Perhaps those screen shots are for an older version? I don't know maybe something has changed or else I'm just blind.

---

### Post by Sef on 2007-12-15
> I looked at that, but the slider bar option for running a dual boot was not an option. Perhaps those screen shots are for an older version? I don't know maybe something has changed or else I'm just blind.

1) Did you md5sum the download?  (Checks to make sure it is good.)

2) Did you burn the disk at 4x or less? (Faster can corrupt the download.)

3) Check the disk for errors.  Instead of clicking Live CD/Install, go down the list; there is an option to check the disk - highlight and click on it.

---

### Post by bobpaul on 2007-12-15
> **The Linguist said:**
> I looked at that, but the slider bar option for running a dual boot was not an option. Perhaps those screen shots are for an older version? I don't know maybe something has changed or else I'm just blind.

It's more likely your ubuntu disk is an older version. When you first boot off the CD it will ask you what you want to do "Boot LiveCD / Install Ubuntu" etc. Press the F1 key. It should say something like> This is a live CD-ROM for Ubuntu
7.10. It was built on 20071016

Make sure you have version 7.10. I just tested my disk, and the option is there. I don't recall if it was for older versions (I thought so, but I don't keep old disks)

If for some reason it still doesn't work, you can manually resize your windows partition using "Partition Editor". It's in the System->Administration menu on the LiveCD. Just resize your windows partition leaving freespace at the end of the disk. Then run the installer and choose "Guided - use the largest continuous free space"

---

### Post by The Linguist on 2007-12-15
> **bobpaul said:**
> It's more likely your ubuntu disk is an older version. When you first boot off the CD it will ask you what you want to do "Boot LiveCD / Install Ubuntu" etc. Press the F1 key. It should say something like

Make sure you have version 7.10. I just tested my disk, and the option is there. I don't recall if it was for older versions (I thought so, but I don't keep old disks)

If for some reason it still doesn't work, you can manually resize your windows partition using "Partition Editor". It's in the System->Administration menu on the LiveCD. Just resize your windows partition leaving freespace at the end of the disk. Then run the installer and choose "Guided - use the largest continuous free space"
I just checked the disc for errors - none

On reboot there was no choice for boot livecd/install ubuntu

but I did get the option to **start or install ubuntu**  would that be the same?

---

### Post by banda on 2007-12-15
run the live cd then goto System->Administration>partition editor....
just right click on the windows partition and choose resize.... enter  the size you want it to be resized to
w8... when its done, go ahead and start the install and choose to use free space for ubuntu..
done!

---

### Post by The Linguist on 2007-12-15
> **bobpaul said:**
> If for some reason it still doesn't work, you can manually resize your windows partition using "Partition Editor". 
It's only giving me 8mb to play with....I can move it to the front of the drive or keep it at the back. Can't resize it any more than that...

---

### Post by Bartender on 2007-12-15
Linguist - 
Can you take a screenshot of the Ubuntu partitioner view and attach it to a post?  Take a screenshot and save it to a thumbdrive, then you can attach it to a post from any PC.  I want to see what you're seeing.

---

### Post by The Linguist on 2007-12-15
Actually I notied a little alert symbol - clicked it and was told the drive physically has errors and to run chkdsk /f /r so I'm doing that now - if it's still problems I guess I'll swap to a newer drive and try installing later.

Right now I'm waiting for chkdsk to finish.

---

### Post by Sef on 2007-12-16
> but I did get the option to start or install ubuntu would that be the same?

Yes, it is.

---

### Post by psychedelix on 2007-12-16
Try using Gutsy Gibbons for your installation.  Use the GUI install.  It is much easier.  Not so many worries.

---

### Post by bobpaul on 2007-12-16
> **The Linguist said:**
> I just checked the disc for errors - none

On reboot there was no choice for boot livecd/install ubuntu

but I did get the option to **start or install ubuntu**  would that be the same?

Sorry, I wasn't very clear. I just meant when you are presented with the menu of choices, press the F1 key on your keyboard. That will let you verify the CD version. Don't choose an option, just press F1.

---

### Post by The Linguist on 2007-12-17
Anyhow sick kids and life has gotten in the way of this installation until after Christmas when I'll have more time. Will post back if I have more trouble.

---

### Post by louieb on 2007-12-17
> **The Linguist said:**
> ...the slider bar ,,, not an option...
You don't alway get the slider bar. It seems to  appear only if the drive has a simple 1 partition scheme. Between now and Christmas might want to read up on partitions.  Their not that hard to figure out. Only 3 types.  
Setting up a PC to dual boot is not that hard but sometimes you got to do a little manual partition preparation. 
Heres a good place to start. [GParted Documentation - general]("http://gparted.sourceforge.net/larry/generalities/gparted.htm")

---

### Post by bobpaul on 2007-12-18
> **louieb said:**
> You don't alway get the slider bar. It seems to  appear only if the drive has a simple 1 partition scheme. 

My laptop has the following partition scheme:
[8 GB NTFS Restore ][ 15 GB NTFS Win ] [11 GB / ]  ( [33GB /home] [2GB Sw] )

When I boot and ran the installer as a test the other day, it offered to resize, but I think it wanted to resize my existing root partion :o

---


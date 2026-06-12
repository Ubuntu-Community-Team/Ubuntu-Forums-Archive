---
title: "Brand new to Ubuntu, want to dual boot on XP, and i have no xp install disks..."
date: 2008-03-09
forum: Absolute Beginner Talk
---

### Post by pete7872 on 2008-03-09
First, the computer I'm going to install this onto:

HP pavillion 7955
XP (SP2)
P4 1.5GHZ, 512 mb Ram
32.8GB Ram, 13.7 Currently free, NTFS filesystem(not sure if that makes a difference)(just defragged)

There is no issue with losing software on the computer(except for one GED practice test program, but I think i can find an alternative)
The issue is that we don't have the XP install disk for a fresh install, but I'm about 90% sure these HP models have a way to revert the PC back to its original factory setup, with as close to a fresh XP install as i can get, but it has all that trial software along with it.

My parents use it basically for internet access and to check their email, real basic things stuff no gaming or programming or anything like that. Is there a tutorial that can show me how to install/partition ubuntu with the current XP set up and without re installing XP?

---

### Post by Barrucadu on 2008-03-09
I've managed to dual-boot XP and Kubuntu on my desktop, so I'll tell you exactly how I did it.

Find and download the Gparted LiveCD ISO. Burn it to disk.
Repeat the above step with the Ubuntu LiveCD ISO.
Put the Gparted LiveCD into the CD drive and reboot the computer.
Right-click on your Windows partition and change "Space After" (I think it's called that, the third box down) to however much space you want for Ubuntu.
In the blank space shown in Gparted, right-click and format it to ext3.
Save the changes and shut down the computer.
Put the Ubuntu LiveCD into the CD drive and start the computer up again.
Go through the install procedure, when you get to the partitioning, click "Manual".
Select the ext3 partition you created in Gparted as the root partition, and finish the installation.
Restart the computer. You can now choose between Ubuntu and Windows in the Grub boot screen.

---

### Post by Rocket2DMn on 2008-03-09
Sure, have a look here: [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
One option is to defrag your windows drive, then resize it from the Ubuntu installer so you don't have to do a fresh XP install.  It doesn't always work, particularly if the drive has had heavy use and can't be defragged enough to make room for Ubuntu, but it is a good option if you don't have an XP disc.

---

### Post by SunnyRabbiera on 2008-03-09
you should not need a xp disk for this, as long as you are careful.
before attempting to set up a dual boot I suggest you do some reading on the subject, there are plenty of guides.
one thing I can personally tell you is please for the love of pete compress your file drive on windows partition and defrag before you do anything.

---

### Post by jken146 on 2008-03-09
> **Barrucadu said:**
> I've managed to dual-boot XP and Kubuntu on my desktop, so I'll tell you exactly how I did it.

Find and download the Gparted LiveCD ISO. Burn it to disk.
Repeat the above step with the Ubuntu LiveCD ISO.
Put the Gparted LiveCD into the CD drive and reboot the computer.
Right-click on your Windows partition and change "Space After" (I think it's called that, the third box down) to however much space you want for Ubuntu.
In the blank space shown in Gparted, right-click and format it to ext3.
Save the changes and shut down the computer.
Put the Ubuntu LiveCD into the CD drive and start the computer up again.
Go through the install procedure, when you get to the partitioning, click "Manual".
Select the ext3 partition you created in Gparted as the root partition, and finish the installation.
Restart the computer. You can now choose between Ubuntu and Windows in the Grub boot screen.

You forgot the swap partition.

---

### Post by anim on 2008-03-09
download and boot with a livecd and everything should be taken care of for you.

when it asks where it should make a linux partition - make sure that "Use Entire Drive" **isn't** selected, and it will add ubuntu to the remaining drive space.

Make sure you leave enough space for you parent's xp installation. And a warning - if you mess something up you may compromise the integrity of the XP install - which means you should probably ask your parents before proceeding.

You can even overwrite the "hidden" partitions that dell/HP use to store the backup of the operating system (which you referenced in your post). Which means XP goes poof! Check to see if you cannot make a backup CD of your operating system. I know Dell lets you make one (and only one) backup in case you loose your HD, but its nice to have regardless.

---

### Post by xc3RnbFO8P on 2008-03-09
> My parents use it basically for internet access and to check their email

I would use the entire disk to Ubuntu.

---

### Post by kindafunnylookin on 2008-03-09
> **Ringi said:**
> I would use the entire disk to Ubuntu.
I don't think this is an appropriate posting. This person is asking how to dual boot. Not how to wipe out XP. Sometimes when you just throw and opinion out there for  a person telling you they are a newbie, sometimes they think you are telling them how to accomplish what they want to do.

---

### Post by xc3RnbFO8P on 2008-03-09
I am just saying  "I would" .
Its only 13 gb free, it means you only got 10 gb to Ubuntu.

---

### Post by forrestcupp on 2008-03-09
> **Barrucadu said:**
> I've managed to dual-boot XP and Kubuntu on my desktop, so I'll tell you exactly how I did it.

Find and download the Gparted LiveCD ISO. Burn it to disk.
Repeat the above step with the Ubuntu LiveCD ISO.
Put the Gparted LiveCD into the CD drive and reboot the computer.
Right-click on your Windows partition and change "Space After" (I think it's called that, the third box down) to however much space you want for Ubuntu.
In the blank space shown in Gparted, right-click and format it to ext3.
Save the changes and shut down the computer.
Put the Ubuntu LiveCD into the CD drive and start the computer up again.
Go through the install procedure, when you get to the partitioning, click "Manual".
Select the ext3 partition you created in Gparted as the root partition, and finish the installation.
Restart the computer. You can now choose between Ubuntu and Windows in the Grub boot screen.

Good guide, but you shouldn't need GParted LiveCD, since Ubuntu's installation includes GParted for the partitioning.  You should be able to do a guided partitioning using the free space on your Windows drive.

---


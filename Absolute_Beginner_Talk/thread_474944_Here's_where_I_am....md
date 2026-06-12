---
title: "Here's where I am..."
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by aheicher on 2007-06-15
Here's where I am

Ready to Install

Your new OS will now be installed with the following settings:

Language: English
Keyboard Layout: US English
Migration Assistant:
Microsoft Windows XP Home Edition (/dev/sda2):(partition #2)

blah blah blah warnings

The partition tables of the following devices are changed
SCSI1 (0,0,0) (sda)

The following partitions are going to be formatted:
partition #1 of SCSI1 (0,0,0) (sda) as swap
partition #3 of SCSI1 (0,0,0) (sda) as ext3




I am trying to install ubuntu with XP on a dual boot and DO NOT want my windows stuff
to be deleted.  Please tell me if I am same.

Thanks
N00B

---

### Post by steve.horsley on 2007-06-15
I can't tell because I don't know what partitions you want to keep, but it looks suspicious that it wants to format partition 1 - the first partition on the disk. That is normally either where windows installs itself, or something like the Dell Utility partition. Think hard before accepting this. You really need to know which partitions are currently in use before using the installer. The live CD has a program called gparted(Gnome Partition Editor) that can display the disk partitions in an easily understood fashion. Use this first to find out what you've got..

If you have data that you cannot afford to have wiped, then abort the install and do a backup first. Now. Right now. There is always a slim chance of a software error even if you manage to avoid user error. We don't want a disgruntled would-be Ubuntu user going round telling everyone that Ubuntu trashed his priceless data.

---

### Post by Golyadkin on 2007-06-15
The partitions to be deleted are on sda, and Windows is on sda2, so you seem to be safe. Maybe someone can confirm this?

---

### Post by Hobo Joe on 2007-06-15
It's says the Windows partition is #2, and that the partitions being formatted(Linux partitions) are #3 and #4.

You'll be fine. I think.... :)


Be sure you defrag Windows several times before messing with partitions.

---

### Post by aheicher on 2007-06-15
my first one is a 49 mb fat 16, and the third is a 3.14 GB ext 3, windows is on second
i only want to keep #2

---

### Post by Golyadkin on 2007-06-15
49 MB, are you sure you mean megabytes?

Maybe you can step back a few steps in the installer and upload a picture of the partition settings.

---

### Post by aheicher on 2007-06-15
give me a minute to get on ubuntu

---

### Post by aheicher on 2007-06-15
first one is the three options and the second is the partitions I have

---


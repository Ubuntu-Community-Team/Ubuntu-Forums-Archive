---
title: "Formating external hdd to ext3?"
date: 2006-07-21
forum: Absolute Beginner Talk
---

### Post by Dinerty on 2006-07-21
I go to System > Administration > Disks > Properties to format my external ntfs hard drive, but the "Format" option is faded?

I can see the hard drive on my gnome desktop and access it fine, but want it to be ext3 :(

---

### Post by Saphira on 2006-07-21
I think you can just fdisk/cfdisk it. 

then you just blow out the partitions, and then reformat it.

---

### Post by coffeecat on 2006-07-21
Use Synaptic to install Gparted. Then use Gparted to partition/format your external usb drive.

I've found it useful to label partitions on USB drives. When they are automagically mounted you get the partition name on your desktop. Unfortunately Gparted doesn't do partition labels (BIG omission, devs!), but you can use the command e2label from a terminal for ext2/3 partitions. Read 'info e2label' or 'man e2label' for all the options.

**Edit:** Sorry - just noticed you're using Kubuntu. Gparted might work under KDE, but if it doesn't, Qtparted should be in the repositories, but I don't think that does labels either. :( :wink:

---

### Post by Dinerty on 2006-07-21
Thanks

Don't I have to right click the drive and click "Eject" on it though, it is a firewire 800 drive?

---

### Post by OU812 on 2006-07-22
If you use cfdisk you may have to do

sudo cfdisk /dev/hdd

or replace hdd with the drive you want to format. If you use something like gparted or qtparted, you will have to unmount the device before you can format it. Don't know about eject though.

john

---

### Post by coffeecat on 2006-07-22
Isn't 'eject' in the GUI the same as unmounting? Yes, I guess you do have to umount/eject an external drive before you can format it. Another way you could do it is to boot up with the Ubuntu live disk which has Gparted at Sytem > Administration > Gnome Partition Editor. Or, if it's the Kubuntu disk you've got, it must have a *parted version on it somewhere.

---


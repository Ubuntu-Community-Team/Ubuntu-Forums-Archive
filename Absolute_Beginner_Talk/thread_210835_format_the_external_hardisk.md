---
title: "format the external hardisk"
date: 2006-07-07
forum: Absolute Beginner Talk
---

### Post by wannabesurfer on 2006-07-07
Hi all
what program can be used in ubuntu to format my external hardisk from ntfs to ext3?

sam:-k

---

### Post by Mike_N on 2006-07-07
I'd just use the G-Parted boot disk but you can install a version of Gparted to Ubuntu and it might be able to help...

-Mike

---

### Post by wannabesurfer on 2006-07-07
there is nothing in synaptic, a easy rogram like in windows to format my external hardisk, clean and easy over to ext3, or is the only version using my boot disk and do it the hard way??

have a great weekend

---

### Post by PriceChild on 2006-07-07
System > administration > disks

Navigate to your device, then to the partition, and on one of the tabs where you choose where to mount it, you may also format it from there.

Be careful and remember to backup all important data as well as double check your actions.

---

### Post by hajk on 2006-07-07
Is the external disk visible from within Ubuntu (either the liveCD or the installed version)? Look at the output in a terminal from the "dmesg | more" command and page through the messages for clues. Is it a USB device? Then you're looking for messages including /dev/sdx where x = {a,b,c,..}.

Once you know the device, you can then repartition and reformat the HD, using  GParted, or doing it the old-fashioned way with the commands in a terminal "sudo cfdisk /dev/sdx" (for partitioning) and "sudo mkfs -t ext3 /dev/sdx" (for reformatting). (Replace x by one of the letters a, b, .. as appropriate).

---

### Post by wannabesurfer on 2006-07-08
I checked in System > administration > disks, found my external hardisk. I tried to format it, but it did not work, it just shows the process line, but nothing is happening. I can choose between ext3 or ext2 among others, also which folder I want. If I would like to use the formated disk for w2k and ubuntu is there a certain setup I should follow.(I have fs installed on w2k)

thanx

---

### Post by hajk on 2006-07-08
You should check that the external disk is NOT mounted, before doing a reformat. By "not mounted" I mean that it should not show up in the file /etc/mtab. You can unmount the disk via the right-click menu, or in a terminal by typing "sudo umount /dev/sdx", where sdx should be replaced by the specific device of the disk. (Note also umount spelling...).

---

### Post by Bloch on 2006-07-08
It has to be unmounted (using umount /dev/hdb or whatever your hard drive is. Or better, rigth click and eject) before you can format. 

If you want to use it for both windows and ubuntu you must use format to FAT32.Cancel all paritions, create one primary partition and format to FAT32

gparted will do it


> there is nothing in synaptic, a easy rogram like in windows to format my external hardisk,


There is! gparted will both partition and format your disk. Look in synaptic.

---

### Post by wannabesurfer on 2006-07-09
how do I use gparted, installed thru synaptic, where do I find it? 

sam

---

### Post by xrchris on 2006-07-09
> **wannabesurfer said:**
> how do I use gparted, installed thru synaptic, where do I find it? 

sam

In Synaptic click search and type gparted. It should then show up. Install it by clicking APPLY. 

Once installed to find the application look in ....

Look in System>Administration>Gnome Partition Editor.

---

### Post by Bloch on 2006-07-09
Ha ha, I was looking in the Applications menu, and eventually just entered
gparted
at the terminal.
If any prog doesn't show up on the menu, you have to start it at the terminal.

---


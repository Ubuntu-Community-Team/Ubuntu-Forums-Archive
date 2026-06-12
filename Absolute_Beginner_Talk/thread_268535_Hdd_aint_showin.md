---
title: "Hdd aint showin"
date: 2006-09-30
forum: Absolute Beginner Talk
---

### Post by haxer on 2006-09-30
How to get hda to show up in desktop so i can put files on it and use it like an normal hdd? Please help need it ;)

---

### Post by xpod on 2006-09-30
I know they show up if mounted in "media".....dont know much more though;)

---

### Post by haxer on 2006-09-30
hmm? how mount?

---

### Post by jaboua on 2006-09-30
You probably wouldn't want the whole hda, you would probably want hda1, hda2 or something like that (partitions on the harddrive hda). What partition do you want to use and what filesystem does it have?

---

### Post by haxer on 2006-09-30
The both got xt3 and its hda i want to use

---

### Post by jaboua on 2006-09-30
In that case try this:
sudo mount -t ext3 /dev/hda /mnt/somefolder

Replace /mnt/somefolder with whereever you want to mount it - as long as the directory exists, it should work.

It is however unusual to use the whole disk as a filesystem, so if it doesn't work I'd suggest running "sudo fdisk -l /dev/hda" to check if it is partitioned (and in that case, what the partitions are called).

Then if it is mounted but doesn't appear on the desktop, just make a shortcut to /mnt/somefolder (or whatever location).

When the disk is properly mounted, report back with what you did so we can create an fstab entry for you (so that the disk automounts at boot)

---

### Post by haxer on 2006-09-30
Dont understand shit sorry dude but keep it simple which folder should i mount (i only want to mount my hdd) and this is the output 

oem@haxer:~$ sudo fdisk -l /dev/hda

Disk /dev/hda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1       24792   199141708+  83  Linux

---

### Post by jaboua on 2006-09-30
OK. There you can see that there is a partition named "hda1" on the harddrive "hda", so that's what we got to mount. Run these commands:

sudo -s
echo /dev/hda1 /media/hda1 ext3 defaults,users 0 2 >> /etc/fstab
mkdir /media/hda1
exit

You should now be able to run "mount /dev/hda1" as a normal user to mount it, and your files should reside in /media/hda1. If an icon doesn't appear on the desktop, you can create a normal shortcut to it - tell me if you don't know how to do that, and in that case also say if you use kubuntu or ubuntu.

---

### Post by haxer on 2006-09-30
Ok now its working fine thanks im using ubuntu 6.06 and i want an dekstop icon:) but one question when i opened my hda1 after compiled it true your instructions i have a file or folder named lost+found whats that?

---

### Post by jaboua on 2006-09-30
If files are corrupted because of an unproper shutdown or something like that, fsck will try to recover them - and might move them into this directory.

BRB with the icon stuff, just got to switch over to the ubuntu box.

---

### Post by haxer on 2006-09-30
when im running fsck i get this 
foem@haxer:~$ fsck
fsck 1.38 (30-Jun-2005)
e2fsck 1.38 (30-Jun-2005)
/dev/hdb1 is mounted.

WARNING!!!  Running e2fsck on a mounted filesystem may cause
SEVERE filesystem damage.

Do you really want to continue (y/n)?


Should i do it?

---

### Post by jaboua on 2006-09-30
No no!! Never fsck a mounted filesystem, that might as the message said  damage the filesystem. Fsck is for fixing a broken filesystem - so don't run it unless the filesystem is broken, and in that case dont' run it with the filesystem mounted. Ubuntu should usually run fsck by itself if it is necesarry during boot.

---

### Post by haxer on 2006-09-30
Ok how about the icon to desktop to hdd ? :P please i understand if you dont want or dont have the energy becouse you helped me so so so much now :) :KS

---

### Post by jaboua on 2006-09-30
Right click the desktop -> Create Launcher

Enter a name, for example "Other Harddrive".
Change "Type" to "Link".
Change "URL" to /media/hda1

Click on "No icon" to select an icon for the disk. If you want the standard disk icons for gnome on ubuntu, enter "/usr/share/icons/Human/scalable/devices" in the text field at the top and then click enter. Then new icons should appear - double click the icon you want. Click on "OK" to create the icon. Voila :P

It's nice helping someone, it's just that I only have KDE on my box so it took some time to switch to a gnome box and make the instructions ;)

---

### Post by haxer on 2006-09-30
Haha.. thank you soooooooo much really nice done didnt think anyone would help me first but there you where :)

---


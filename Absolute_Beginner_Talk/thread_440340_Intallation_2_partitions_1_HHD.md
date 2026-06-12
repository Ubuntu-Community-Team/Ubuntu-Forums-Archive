---
title: "Intallation 2 partitions 1 HHD"
date: 2007-05-11
forum: Absolute Beginner Talk
---

### Post by frigin_AL on 2007-05-11
I have a Compaq Presario - Laptop
1.7Ghz - 1Gb Ram
80GB partitioned like this= 10GB Windows XP & 69GB for the rest of my files (docs, mp3, etc)

I would like to install Ubuntu 7.4:
- I dont mind Giving 10GB to Ubuntu and leaving the rest for Win
- I would like to keep my files

(Newbie here last question: if I deleted the partition, can I have/crate: 10GB for Ubuntu and the rest for win? without loosing my files, mp3, etc??)

Soo many questions No soo much time..!

---

### Post by Rescue9 on 2007-05-11
While many people may tell you that resizing your partitions with information on them is a viable option, I wouldn't try it myself. I've done it both ways, and lost a good deal of information.

What I suggest you do is find a way to transfer the information from your "data" partition off, then split the data partition again. This way you can have 10G Windoze, 10G Ubuntu, and the rest as "data". One thing to remember though.. you'll want to setup a swap partition to make things run smoother. With hdd space coming so cheaply now, i'd suggest a 500M - 1G partition.

Remember this though!!!! Once you delete your partition to resize it, ALL information on that partition will go buy bye!

---

### Post by Ianman on 2007-05-11
You can resize a partition (even with files on it) but to be perfectly honest, I always find this risky. It has happened too many times to me that I have resized a partition and lost some or all of the data on the partition :(

What I suggest is that you backup the stuff on the 69GB parition (I am assuming it is not entirely full). Then delete the partition and create a new partition in windows for windows leaving unused space for linux. Then when you install Linux, select the unused space and let Linux partition it for you.

If you don't really know what you are doing this would be the safest way I think. If this is your first Linux install, try not to get into Partition too much just yet!

---

### Post by frigin_AL on 2007-05-11
Excellent.

Guys, you saved my life (read it: files)... I think I'll make a backup and format the HDD, install Win XP on the whole 80Gb, and the use Ubuntu partition thing and install...

A new install is needed anyway! 
By the way, should I do it like that? reformat to 80gb, intall win and then linux? recomemdation welcome

---

### Post by frigin_AL on 2007-05-11
I forgot to mention that I need to have more than 10gb on win, because when trying to burn dvd, the nero cant use the temp folder! TO SMALL.... I tried to set it up to use the 2nd partition, didnt work (read it: I was lazy I couldnt find the file that route the temp file to the win partition!) 
Damn win!

---

### Post by hyper_ch on 2007-05-11
Resizing - normally - not be any problem. Just make sure, when you are using ntfs that you defrag the partition at least twice before you want to resize it.....
Resizing a partition can take several hours... so be patient...

and the most important thing:

**MAKE BACKUPS BEFORE MESSING AROUND WITH PARTITIONS!**

well, it's a good idea to make also backups on a regular base if you are not resizing... but that's another topic.

---

### Post by Ianman on 2007-05-12
Yes always install Windows first. Linux recognizes the Windows installation and creates a bootloader so that you can select which OS you would like to use when you turn the computer on. If you Install Linux first and then windows, windows simply overwrites the boot sector of your HD and you can't get to ur Linux partition! (Damn microsoft).

I would recommend the partitioning like this:

Windows 20GB
Other windows stuff 40GB
Linux 20GB

That way Nero will have no problems and 20GB in Linux will give you enough room to mess around with installing programs and the like. I tried it with only 15GB once but ran out of room real fast.

I hope this helps.

---

### Post by Rescue9 on 2007-05-12
Getting to linux after a windoze install is simply a matter of booting from the LiveCD, ```
mount -t none /dev/proc /YOURCHROOTDIR/proc
``` and ```
mount -o bind /dev /YOURCHROOTDIR/dev
```. After that chroot into your linux root partition and run ```
grub-install /dev/YOURMBRDRIVE
```. Sometimes grubinstall doesn't work so you have to run the setup from within grub. I'm sure you can find those instructions

---


---
title: "2nd HDD, /etc/fstab"
date: 2006-08-08
forum: Absolute Beginner Talk
---

### Post by PBeck929 on 2006-08-08
Hi all, I have Xubuntu installed on a 74gb hdd and I have a 320gb storage drive that I want to implement, but there is no line in my /etc/fstab file and I know my computer 'sees' it, but I can't figure out how to make it work.  I have the second hdd set on slave.  When I go into System>Disks, it's there, but I can't seem to access it any way any how...

Here is my /etc/fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0     1
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       
/dev/sda5       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0


My question is, what kind of entries would I make in my /etc/fstab file to make this drive work properly?  Thanks for your help...

---

### Post by anaconda on 2006-08-08
What kind of hd is your storage hd?

is it external USB-hdd
is it IDE
or SATA

what filesystem is in your hd? is it ntfs, fat32 or ext3 ?
they are mounted differently.

you can try to mount it manually before touching your fstab-file.


first create the directories you try to mount to: (if they dont exist already..)
sudo mkdir /mnt/hdb1
sudo mkdir /mnt/sdb1
 
then try to mount:
for a ide drive:
sudo mount -t auto /dev/hdb1 /mnt/hdb1
for a sata or USB drive:
sudo mount -t auto /dev/sdb1 /mnt/sdb1

then go to /mnt/sdb1 (or /dev/hdb1) to look if your drive is there...

---

### Post by PBeck929 on 2006-08-08
ok that worked...now does that mean I have to manually mount it everytime I restart?

---

### Post by anaconda on 2006-08-08
Now that you know that it works, you can modify your fstab-file accordingly.. (make a backup first)
It is almost the same mount command, but in different order

if this was how you mounted it:
sudo mount -t auto /dev/sdb1 /mnt/sdb1

then you would have to add (for example) this line to your fstab-file.

/dev/sdb1   /mnt/sdb1   auto   defaults   0   2

But you should change the "auto" to whatever filesystem the disk is formatted to.
if the filesystem is:
fat32  change auto to vfat
ntfs   change auto to ntfs
ext3   change auto to ext3

---

### Post by PBeck929 on 2006-08-08
Thank you very much anaconda... that worked perfectly.  I tried to mess with the /etc/fstab and I had everything just the way you said it except at the end I had "0   1" instead of "2", so again, thank you very much...

---


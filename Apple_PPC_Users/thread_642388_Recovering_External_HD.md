---
title: "Recovering External HD"
date: 2007-12-16
forum: Apple PPC Users
---

### Post by Kopachris on 2007-12-16
I recently backed up my data and reloaded my Mac (PowerBook G4) and now the external hard drive (190GB Maxtor 3200) won't mount in OS X.  It automatically mounts on the Ubuntu Edgy live CD, though, so I want to use the live CD (don't want to actually install Ubuntu as networking is still shaky due to firewalling I think (can you just get rid of the firewall?  The computer with the router has a firewall to protect the network, I don't need one on my comp too)) to recover my data, but I don't know how to mount my HFS+ partition that has Mac OS X.  The partition is /dev/hda3.  How do I mount an internal partition from the live CD?

---

### Post by frog_pilot on 2007-12-16
What do you have as file system on your external hd. writing on hfs+ volumes from ubuntu is not working out of the box. on journaled hfs+ (as your osx system volume is) you can't write from ubuntu at all. there is a workaround but its a little bit tricky and not realy save.

If your external hd is formated in ext3 you could use [ext2fsx]("http://sourceforge.net/projects/ext2fsx/") to access it from osx.

---

### Post by Kopachris on 2007-12-16
I figured that out now...  I mounted the hfs+ and it wouldn't write or change owners.  So I used GParted to format the ext3 that I was going to use for Linux From Scratch into a fat32 and copied the data from the MAXTOR over to it.  Now I have to figure out how to mount disk0s2, the fat32 part, in OS X so I can recover the data.

---

### Post by frog_pilot on 2007-12-17
[there is a problem with fat32 partitions created by parted. Osx wont recognize the file system. I dont know why. but it seems there is a problem with the parted changes to the partition table. osx wont recognize them right.

i had the same problem when i created a fat32 volume beside my osx system volume with parted. in osx disk utility it showed strage data and didnt recognize the file system. i think it depends on the free spaces between the apple volumes. like in your case, in my the fat32 was also hda2 and osx was hda3. I had to delete hda2 with gparted and to boot from osx install dvd to create a volume with the disk utility from the install dvd. There was no way to access the fat32 volume.

try it on another pc. copy your data to it. create fat32 volume under windows. this should work.

To copy the data with the live cd there is a way.
You have to disable the journaling on your osx volume. in osx open a terminal and execute ```
sudo dikutil disableJournal /
```
then you have to start from the live cd and install 2 packages for hfs-support. I cant find out the correct names right now. but i know you need exactly 2 packages for hfs write support. try searching for hfs in synaptics.
after this you can mount your osx volume and write to it.

to turn on your diskjournal after the procedure execute ```
sudo dikutil enableJournal /
``` from osx.

---

### Post by Kopachris on 2007-12-19
Thanks anyway.  I created a disk image of the FAT32 partition and then mounted the image and it worked.  I have all my data back.

---


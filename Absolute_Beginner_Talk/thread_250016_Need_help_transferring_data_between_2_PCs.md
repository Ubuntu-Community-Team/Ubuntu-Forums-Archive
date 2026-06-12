---
title: "Need help transferring data between 2 PCs"
date: 2006-09-03
forum: Absolute Beginner Talk
---

### Post by Amorphous_Snake on 2006-09-03
The first is using Ubuntu 6.06. The second one has an Ubuntu LiveCD 6.06.
I have set up the first to have the home folder shared. And made the IP address as 192.168.0.2 with a subnet mask 255.255.255.0 and a gateway 192.168.0.1.

As you have guessed 192.168.0.1 is the second system.

When I run the LiveCD in the second system, how can I mount the partitions of this PC (FAT32) and (NTFS)? I just want to copy data, I don't want to write anything on the second system.

Help please!

---

### Post by xyz on 2006-09-03
Could this be what you're looking for:
[http://digen.wordpress.com/2006/04/28/configuring-nfs-server/](http://digen.wordpress.com/2006/04/28/configuring-nfs-server/)

---

### Post by steve.horsley on 2006-09-03
Use the command **sudo fdisk -l **to find out what the partition names are. Using this information, use commands like this to mount them. As an example, I assume that hda1 is NTFS and hda2 is FAT:
[B]sudo mkdir /media/hda1
sudo mkdir /media/hda2
sudo mount -t ntfs -o nls=utf8,umode=222 /dev/hda1 /media/hda1
sudo mount -t vfat -o nls=utf8,umode=222 /dev/hda2 /media/hda2[/B]

For reference:
[http://ubuntuguide.org/wiki/Dapper#Windows](http://ubuntuguide.org/wiki/Dapper#Windows)

Hope this helps

---


---
title: "fsck error during startup !"
date: 2007-01-13
forum: Absolute Beginner Talk
---

### Post by findik1 on 2007-01-13
Hi,
Ubuntu keeps gibing error during startup:
[I]Log of fsck -C -R -A -a
Fri Jan 12 17:55:18 2007

fsck 1.39 (29-May-2006)
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
/dev/sda2: 6849 files, 1060112/1278917 clusters
fsck.ext3: Unable to resolve 'UUID=9617953f-c14f-462b-8ab5-2bfceddbf284'
fsck died with exit status 8[/I]

I looked this forum and very similar error to mine, but still did not understand howto resolve it: [http://www.ubuntuforums.org/showthread.php?t=333323&highlight=fsck](http://www.ubuntuforums.org/showthread.php?t=333323&highlight=fsck)

If I type: 
ls /dev/disk/by-uuid/ -alh 
I get:
[I]total 0
drwxr-xr-x 2 root root 140 2007-01-12 17:55 .
drwxr-xr-x 6 root root 120 2007-01-12 12:55 ..
lrwxrwxrwx 1 root root  10 2007-01-12 17:55 1B33-0A00 -> ../../sda2
lrwxrwxrwx 1 root root  10 2007-01-12 17:55 25aaea84-fb54-4d92-97aa-10410840e478 -> ../../sda5
lrwxrwxrwx 1 root root  10 2007-01-12 17:55 5ef0eb00-5ab2-4491-ba7d-d3b21e763938 -> ../../sda3
lrwxrwxrwx 1 root root  10 2007-01-12 17:55 664C41F04C41BC15 -> ../../sda1
lrwxrwxrwx 1 root root  10 2007-01-12 17:55 c71d7c64-263d-4a81-b4e7-e22ff0799a60 -> ../../sda6[/I]

I type: 
cat /etc/fstab  
I get:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=5ef0eb00-5ab2-4491-ba7d-d3b21e763938 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=664C41F04C41BC15 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=1B33-0A00  /media/sda2     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=9617953f-c14f-462b-8ab5-2bfceddbf284 /media/sda5     ext3    defaults        0       2
# /dev/sda6
UUID=c71d7c64-263d-4a81-b4e7-e22ff0799a60 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

=====================================
You may ask after when this happened????
Here is what I did before this error occurred:
I reinstalled ubuntu on different partition. Originally I had ubuntu in dev/sda5, while dev/sda1 was windows and sda3 was extra linux partition left when I shrinked dev/sda1 and formatted to linux partition to become /dev/sda3. I made a mistake in linux (long story) so I decided to install ubuntu on sda3, and I have been using this ubuntu since then. After I tranferred my files from /sda5 ubuntu, I decided to reformat /sda5 naturally. Attached is the current partition (screenshot.png).

Partition shows that linux swap is /sd6 (as if left from the previous ubuntu install, it is just nect to sda5). Should I make a new swap next to sda3? How much size should I give, 600 mb seems small.
thank you,
findik

---

### Post by findik1 on 2007-01-13
This issue is solved. See the link if you have similar problem.
[http://www.ubuntuforums.org/showthread.php?t=337235](http://www.ubuntuforums.org/showthread.php?t=337235)
Also this link should help you too:
[http://www.ubuntuforums.org/showthread.php?t=333323&highlight=fsck](http://www.ubuntuforums.org/showthread.php?t=333323&highlight=fsck)

Thank you very much ubuntu community. People are really helpful for  a linux beginner!

---


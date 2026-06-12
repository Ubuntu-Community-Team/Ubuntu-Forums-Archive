---
title: "changing permissions on ntfs drive"
date: 2007-06-14
forum: Absolute Beginner Talk
---

### Post by natakim on 2007-06-14
hi all. i think i need some help. i've been trying to change the permissions on an internal ntfs drive. at present i have read only. i'm attempting to change the owner to me. have been following instructions in other threads but to no success so far.

**sudo fdisk -l**

> Disk /dev/sda: 250.0 GB, 250059350016 bytes
16 heads, 63 sectors/track, 484521 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      484521   244198552+  42  **SFS**

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001   83  Linux

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       38913   312568641    7  HPFS/NTFS

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       14593   117218241    7  HPFS/NTFS

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        9327    74919096   83  Linux
/dev/hdb2            9328        9729     3229065    f  W95 Ext'd (LBA)
/dev/hdb5            9328        9729     3229033+  82  Linux swap / Solaris

for some reason the disk is marked here as SFS

i've tried...

**sudo chown -R natakim:natakim /media/movies**

> tem
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP162/A0032173.ico': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP162/A0032174.ico': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP162/A0032175.ico': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP162/A0032176.ico': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP162/A0032177.ico': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP162/A0032179.ico': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP162/A0032180.ico': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP162/A0032181.ico': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP162/A0032182.ico': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP162/A0032183.ico': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP162/A0032184.ico': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP162/A0032185.ico': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP162/A0032186.ico': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP162/A0032187.ico': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP162/A0032188.ico': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP162/A0032189.ico': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP162/A0032190.ico': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP162/A0032191.ico': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP162/A0032192.ico': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP162/A0032193.ico': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP162/A0032194.ico': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP162/A0032195.ico': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP162/A0032197.ico': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP162/A0032198.ico': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP162/A0032199.ico': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP162/A0032200.ico': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP162/A0032201.ico': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP162/A0032202.ico': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP162/A0032203.ico': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP162/A0032204.ico': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP162/A0032205.ico': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP162/A0032206.ico': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP162/A0032207.ico': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP162/A0032208.ico': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP162/A0032209.ico': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP162/A0032210.ico': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP162/A0032211.ico': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP162/A0032212.ico': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP162/A0032213.ico': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP162/A0032215.ico': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP162/A0032216.ico': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP162/A0032217.ico': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP162/A0032218.ico': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP162/A0032219.ico': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP162/A0032220.ico': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP162/A0032221.ico': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP162/A0032222.ico': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP162/A0032223.ico': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP162/A0032224.ico': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP162/A0032225.ico': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP162/A0032226.ico': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP162/A0032227.ico': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP162/A0032228.ico': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP162/A0032229.ico': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP162/A0032230.ico': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP162/A0032231.ico': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP162/A0032233.ico': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP162/A0032234.ico': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP162/A0032235.ico': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP162/A0032236.ico': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP162/A0032237.ico': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP162/A0032238.ico': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP162/A0032239.ico': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP162/A0032240.ico': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP162/A0032241.ico': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP162/A0032242.ico': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP162/A0032243.ico': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP162/A0032244.ico': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP162/A0032245.ico': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP162/A0032246.ico': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP162/A0032247.ico': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP162/A0032248.ico': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP162/A0032249.ico': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP162/A0032251.ico': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP162/A0032252.ico': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP162/A0032253.ico': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP162/A0032254.ico': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP162/A0032255.ico': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP162/A0032256.ico': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP162/A0032257.ico': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP162/A0032258.ico': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP162/A0032259.ico': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP162/A0032260.ico': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP162/A0032261.ico': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP162/A0032262.ico': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP162/A0032263.ico': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP162/A0032264.ico': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP162/A0032265.ico': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP162/A0032266.ico': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP162/A0032267.ico': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP162/A0032269.ico': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP162/A0032270.ico': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP162/A0032271.ico': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP162/A0032272.ico': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP162/A0032273.ico': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP162/A0032274.ico': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP162/A0032275.ico': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP162/A0032276.ico': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP162/A0032277.ico': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP162/A0032278.ico': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP162/A0032279.ico': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP162/A0032280.ico': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP162/A0032281.ico': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP162/A0032282.ico': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP162/A0032283.ico': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP162/A0032284.ico': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP162/A0032285.ico': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP162/A0032286.ico': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP162/A0032287.ico': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP162/A0032288.ico': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP162/A0032289.ico': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP162/A0032290.ico': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP162/A0032291.ico': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP162/A0032292.ico': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP162/A0032293.ico': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP162/A0032294.ico': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP162/A0032295.ico': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP162/A0032296.ico': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP162/A0032297.ico': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP162/A0032298.ico': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP162/A0032299.ico': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP162/A0032300.ico': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP162/A0032301.ico': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP162/A0032302.ico': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP162/change.log': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP162': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP75/A0008217.ini': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP75/change.log.1': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP75/RestorePointSize': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP75': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP76/A0008291.exe': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP76/A0008244.ini': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP76/A0008275.ini': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP76/A0008276.exe': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP76/A0008277.exe': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP76/A0008278.nfo': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP76/A0008279.msi': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP76/A0008280.NFO': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP76/A0008281.nfo': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP76/A0008282.exe': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP76/A0008283.exe': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP76/A0008284.nfo': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP76/A0008285.exe': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP76/A0008286.exe': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP76/A0008287.exe': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP76/A0008288.exe': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP76/A0008289.exe': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP76/A0008290.exe': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP76/A0008292.exe': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP76/A0008293.exe': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP76/A0008294.exe': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP76/A0008295.ini': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP76/A0008296.inf': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP76/A0008297.msi': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP76/A0008298.exe': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP76/A0008299.dll': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP76/A0008300.dll': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP76/A0008301.exe': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP76/A0008302.exe': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP76/A0008303.exe': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP76/A0008304.nfo': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP76/change.log.1': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP76/change.log.2': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP76/RestorePointSize': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}/RP76': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information/_restore{0FB50533-A786-4600-9ECF-E589ECE75241}': Read-only file system
chown: changing ownership of `/media/movies/System Volume Information': Read-only file system
chown: changing ownership of `/media/movies/Thumbs.db': Read-only file system
chown: changing ownership of `/media/movies': Read-only file system


then...

**ls -la /media**

> total 40
drwxr-xr-x  8 root    root    4096 2007-06-14 14:48 .
drwxr-xr-x 23 root    root    4096 2007-06-05 00:48 ..
lrwxrwxrwx  1 root    root       6 2007-05-02 19:33 cdrom -> cdrom0
drwxr-xr-x  2 root    root    4096 2007-05-02 19:33 cdrom0
drwxrwxr-x 14 natakim natakim 4096 2007-06-11 17:27 drive
drwxrwxrwx  1 root    root    4096 2007-06-04 08:58 games
-rw-r--r--  1 root    root     252 2007-06-14 14:48 .hal-mtab
--wxr-x---  1 root    root       0 2007-04-15 21:56 .hal-mtab-lock
drwx------  2 root    root    4096 2007-06-06 22:10 I_ROBOT_SPECIAL_EDITION_DISC_1?
dr-xr-xr-x  1 root    root    4096 2007-06-14 13:25 movies
drwxrwxrwx  1 root    root    8192 2007-06-14 13:18 windowz


but it doesn't change the disk ownership.


any suggestions where i'm going wrong? please.

edit: if it's any help i get this...

> # /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/hdb1 :
UUID=d4dd4784-d599-4d37-b926-b0a5c62f4dfc / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/hdb5 :
UUID=439f0f72-7e22-4be2-89cc-6df98d2ccfa8 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/hda1 /media/windowz ntfs-3g defaults,locale=en_AU.UTF-8 0 0
/dev/sdb1 /media/drive ext3 defaults 0 0

from 
[B]
sudo gedit /etc/fstab[/B]

---

### Post by natakim on 2007-06-14
could it be because the drive is listed as SFS?

i installed automatix2,(hope it doesn't cause hell with ntfs config tool running also), but the drive is still not writable.

---

### Post by Madmoose on 2007-06-14
You know, about three days ago I lost permissions on my slave drive. It was working one day, and the next the ownership was switched to root. 

Anyway ideas?

---

### Post by natakim on 2007-06-14
i just found this thread, might try as advised in there

[http://ubuntuforums.org/showthread.php?t=328351&highlight=SFS+format]("http://ubuntuforums.org/showthread.php?t=328351&highlight=SFS+format")

edit: actually sda1 doesn't show on

sudo gedit /etc/fstab

---

### Post by Madmoose on 2007-06-19
I don't think that applies to what I'm looking for.

---


---
title: "Clementine can't add files to Ipod Classic"
date: 2013-04-22
forum: Apple Hardware Users
---

### Post by Jonno303 on 2013-04-22
[COLOR=#333333][FONT=Ubuntu Beta]Ubuntu 12.04 64 bit, Clementine 1.01[/FONT][/COLOR]

I'm unable to add files to my ipod classic 80gb using "copy to device" (or any other method). I can play existing music from the Ipod through Clementine, but unable to add/edit/delete files. I receive the following message:


Error opening '/media/0a09c861-cfcf-34bf-8908-fd0184a78044/iPod_Control/Music/F36/libgpod702580.mp3' for writing (Read-only file system).With ipod connected I ran:


dfFilesystem 
    1K-blocks     Used Available Use% Mounted on/dev/sda6       30479304 12696156  16234860  44% /udev             3860960        4   3860956   1% /devtmpfs            1548112      960   1547152   1% /runnone                5120        0      5120   0% /run/locknone             3870276      372   3869904   1% /run/shm/dev/sdb3       77953984 31709568  46244416  41% /media/0a09c861-cfcf-34bf-8908-fd0184a78044 

sudo fdisk -lDisk /dev/sda: 
256.1 GB, 256060514304 bytes255 heads, 63 sectors/track, 31130 cylinders, total 500118192 sectorsUnits = sectors of 1 * 512 = 512 bytesSector size (logical/physical): 512 bytes / 512 bytesI/O size (minimum/optimal): 512 bytes / 512 bytesDisk identifier: 0x4bd72476   Device Boot      Start         End      Blocks   Id  System/dev/sda1   *        2048     3074047     1536000    7  HPFS/NTFS/exFAT/dev/sda2         3074048   151064575    73995264    7  HPFS/NTFS/exFAT/dev/sda3       151066622   483338239   166135809    f  W95 Ext'd (LBA)/dev/sda4       483338240   500115455     8388608   84  OS/2 hidden C: drive/dev/sda5       151066624   405514239   127223808    7  HPFS/NTFS/exFAT/dev/sda6       405516288   467447807    30965760   83  Linux/dev/sda7       467449856   483338239     7944192   82  Linux swap / SolarisNote: sector size is 2048 (not 512)Disk /dev/sdb: 80.0 GB, 80026361856 bytes255 heads, 63 sectors/track, 2432 cylinders, total 39075372 sectorsUnits = sectors of 1 * 2048 = 2048 bytesSector size (logical/physical): 2048 bytes / 2048 bytesI/O size (minimum/optimal): 2048 bytes / 2048 bytesDisk identifier: 0x00000000Disk /dev/sdb doesn't contain a valid partition table

I suppose this is a permissions issue with the ipod, but I can't figure out how to change them.

---

### Post by Jonno303 on 2013-04-24
bump

---

### Post by Jonno303 on 2013-04-26
I have had no luck with this problem and have now switched music players. 


No problem at all with Guayadeque 0.3.5. I highly recommend it as a player and ipod organizer.


For those who make the switch to Guayadeque: download it through the Ubuntu software center, but make sure you also run: sudo apt-get install libgpod-dev in the terminal to get ipod support. Once your ipod icon turns up, just right click on it and "update" it. 


Clementine looked to be an excellent music player, but I had no solution to my problem. I have no regrets about making the switch to Guayadeque, however.

---


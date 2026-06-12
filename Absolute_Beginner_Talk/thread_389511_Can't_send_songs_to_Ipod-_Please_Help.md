---
title: "Can't send songs to Ipod- Please Help"
date: 2007-03-20
forum: Absolute Beginner Talk
---

### Post by dcbtfoabaaposba7 on 2007-03-20
Hey, i've been trying for a very long time to get my ipod (2nd gen) to work with ubuntu. I've read through many of other posts regarding the same issue, but i still can't seem to fix it. When i plug my ipod into my computer it is instantly recognized by rythmbox and my ipod shows up on my desktop. I just can't send songs to my Ipod. 

If i try to send a song through rythmbox i get this error. 
Could not open file "/media/ipod/iPod_Control/Music/F01/02-sigur_ros.mp3" for writing.

I've also tried to use gtkpod and i receive this error.

"You did not import the existing iTunesDB ('/media/ipod/iPod_Control/iTunes/iTunesDB'). This is most likely incorrect and will result in the loss of the existing database."

If i proceed i get this error. 

"Error opening '/media/ipod/iPod_Control/Music/F13/gtkpod467620.mp3' for writing (Read-only file system)."

I guess changing it from a Read-only filesystem would help- but i dont know how to do this.

I read that using 

[HTML]sudo dosfsck -a /dev/sda2[/HTML]

would help, but my ipod doesnt mount on dev/sda2 becuase i get this error-

[HTML]dosfsck 2.11, 12 Mar 2005, FAT32, LFN
open /dev/sda2:No such file or directory[/HTML]

How can i find what my ipod mounts to? is that all i have to do for it to start importing songs correctly? Please help in any way- I've been trying to get this to work for a very long time and just now has my frustration made me ask for help. Thanks in advance.

---

### Post by aysiu on 2007-03-21
Sounds as if your iPod isn't getting mounted properly for some strange reason.

This may help (make sure your iPod is plugged in first):
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by dcbtfoabaaposba7 on 2007-03-21
thanks for the reply. I tried to do as you said and got these results.

[HTML]nathaniel@nathaniel-desktop:~$ sudo umount /media/ipod
nathaniel@nathaniel-desktop:~$ sudo fdisk -l

Disk /dev/hda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1       17793   142922241   83  Linux
/dev/hda2           17794       19098    10482412+  82  Linux swap / Solaris
/dev/hda3           19099       24320    41945715   83  Linux

Disk /dev/sde: 10.0 GB, 10000005120 bytes
255 heads, 63 sectors/track, 1215 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1           5       40131    0  Empty
/dev/sde2               6        1215     9719325    b  W95 FAT32
[/HTML]

I changed my fstab to this

[HTML]# /etc/fstab/: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=8cee63ab-ef39-4b5c-addc-ac3e6cb81b78 /               ext3    defaults,erro$
# /dev/hda3
UUID=8ab7e550-8918-46fc-ae7a-044f9c217e08 /media/hda3     ext2    defaults     $
# /dev/hda2
UUID=9b22e92c-0921-4872-8206-341167b19d2b none            swap    sw           $
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0

/dev/sda2 /fat_files vfat iocharset=utf8,umask=000 0 0
[/HTML]

I changed the bottom one which my ipod is connected to fat_files becuase my ipod is in FAT32.

when i sudo mount -a 

it said the directory doesnt exist...

what did i do wrong- should i try something else. thank you so much.

---

### Post by kpkeerthi on 2007-03-21
/fat_files must exist before you mount to it..

sudo mkdir /fat_files

---

### Post by dcbtfoabaaposba7 on 2007-03-21
alright thanks. I got it to mount like that. 
But i still get the same error.

something like

Could not open file "/media/ipod/iPod_Control/Music/F01/02-sigur_ros.mp3" for writing.


is there anything else i should try? Thanks a lot for the replys.

---


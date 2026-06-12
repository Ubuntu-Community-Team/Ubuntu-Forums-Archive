---
title: "How do my drives on Ubuntu"
date: 2006-12-01
forum: Absolute Beginner Talk
---

### Post by Scottty on 2006-12-01
Hello

Well I did it!!! I made the switch!!, I changed my main O/S to Ubuntu. Now I want to become familiar where everything is. Specifically I want to see if I can see where my Windows Partitions are (Because I save my important files on one of my drives. I also want to locate my Lyra Mp3 player to see if it is rcognized (It uses Fat 32).

I have looked in Places > Computer and all I have there is Floppy 1, CD/DVD ROM and Filesystem but there is now C: drive D Drive etc or do they exist in Linux?

I would prefer to view them with GUI rather than command line if possible?

Thanks
Scott

---

### Post by reiki on 2006-12-01
your windows partitions don't show up in Places because they are not mounted (at least that's my assumption)

if you open a terminal and type     mount
I think it will show you all the stuff Ubuntu found even if it's not mounted.

In linux basically everything is files. Partitions are "files". But they have to be mounted. Your root partition is being mounted at boot time automatically and your CD drive shows up because Ubuntu knows it's there and when you actually stick a CD in it, it will get mounted. :)

This isn't real hard, but I'm probably not explaining it real well either. 

So look around for how to mount things, and what mount points are, and if your windows partitions are NTFS you may want to look into reading NTFS format in linux. Like I said.... not hard, but different if you've not done it before. And if those windows partitions are going to stay there you can make this such that they will be mounted at boot time. 

As an example I have 2 hard drives in my machine. One is IDE and the other is SATA. Both have Ubuntu (different version) but...

The IDE is /dev/hda1 and gets mounted as / when I boot Dapper. The SATA drive is /dev/dsa1 and gets mounted as /SATAdrive when I boot Dapper. So I have access to both drives.

When I boot Edgy /sev/sda1 is mounted as / and /dev/hda1 gets mounted as /IDEdrive. 

:)

Are we shedding light? Or are we confusing you?

---

### Post by Hankers on 2006-12-01
This may help you. Using the instructions there I had no problems with accessing info on an NTFS drive.
[http://www.psychocats.net/ubuntu/mountwindows.php](http://www.psychocats.net/ubuntu/mountwindows.php)

Hope this is what you are looking for.

---

### Post by Scottty on 2006-12-01
I went to [http://www.psychocats.net/ubuntu/mountwindows.php](http://www.psychocats.net/ubuntu/mountwindows.php)
and started the tutorial

first I typed sudo fdisk -l
and got the following 
> 
Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        2761    22177701    7  HPFS/NTFS
/dev/hda2            3780        4865     8723295    f  W95 Ext'd (LBA)
/dev/hda3   *        2762        3779     8177085   83  Linux
/dev/hda5            3828        4865     8337703+   7  HPFS/NTFS
/dev/hda6            3780        3827      385497   82  Linux swap / Solaris

Partition table entries are not in disk order
Note: sector size is 2048 (not 512)

Disk /dev/sda: 1045 MB, 1045430272 bytes
16 heads, 32 sectors/track, 997 cylinders
Units = cylinders of 512 * 2048 = 1048576 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         997     1020864    b  W95 FAT32
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(0, 0, 32) logical=(0, 1, 1)



From there they want me to edit the fstab file and this is what I see
in Nano

> 
  GNU nano 1.3.12             File: /etc/fstab                                  

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3
UUID=cee4118a-34c2-44e7-b233-d1b06af34967 /               ext3    defaults,erro$
# /dev/hda6
UUID=16a0a389-6ff9-484d-9ac6-c2a7fe29ff2a none            swap    sw           $
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0



There doesn't seem to be able to change anything in this file because my
NTFS files don't show up.

Do you have any suggestions?

Scott

---

### Post by quarkhirad on 2006-12-01
Dear scottty

Yes here is ur solution and this should work because i use it to mount all my  windows partitions each time i boot up. 

You will have to work in terminal initially and then u can get a gui 

I shall give you a step by step assuming u are absolutly a fresher 
Note:
1) anything in () is a comment for u and is not to be typed.
2) please replace khirad with ur user name and Elli with ur computer name

first open terminal
(it will give u a window with the following where khirad is my username and elli is my comp name )

khirad@Elli:~$

(At this prompt type the following.) 

khirad@Elli:~$sudo su (press enter)
password:(type in ur password and then press enter) 
root@Elli:/home/khirad# mkdir /home/khirad/c_drive (now press enter)
root@Elli:/home/khirad# mkdir /home/khirad/d_drive (now press enter)
root@Elli:/home/khirad# mount /dev/hda1 /home/khirad/c_drive (now press enter)
root@Elli:/home/khirad# mount /dev/hda5 /home/khirad/d_drive (now press enter)
root@Elli:/home/khirad# nautilus (press enter)
(you will get a seperate gui application. after this opens press and hold   the ctrl key and then press l. After pressing l releaase both the keys and enter the following /home/khirad/ and then press enter. You will get some folders and files(if you have created any) open the folder c_drive to browse ur C drive and open d_drive to browse ur D drive. There will be a tool bar on top which u can use to go back, forward, up one level etc. The buttons look like there conterparts in windows and are even labled)   

( NOTE: U WILL NOT BE ABLE TO CREATE FOLDERS,FILES IN UR C AND D DRIVE THROUGH LINUX. This is because ur partition is NTFS type and ubuntu doesn't support writing to NTFS type file system. However u can view and read the contents of ur C and D drives. also note DO NOT quit the terminal in which you typed the command nautilus.If u do so it will close ur file browser.)


Thats all buddy. Hope this guide was good enough for u. All the best. 
If you have any probs u can mail me at [email]quarkhirad@gmail.com[/email] 
please keep the subject as "mounting file systems in ubuntu"
Thanks 

cheers 
all the best

---

### Post by peabee on 2006-12-03
This is the one...
I've finally managed to mount my Windows partition so I can see it. 
Thank you
(yet another bookmark in 'Ubuntu for simple people like me' folder)

---

### Post by quarkhirad on 2006-12-07
> **peabee said:**
> This is the one...
I've finally managed to mount my Windows partition so I can see it. 
Thank you
(yet another bookmark in 'Ubuntu for simple people like me' folder)

Hey ur welcome no probs even when i was a beginner i had the same problem. Thanks 
;) 
Cheers 

khirad

---

### Post by robinl on 2006-12-07
It would be better if you just put it in /etc/fstab so it will automatically be mounted every time you boot. Just copy these lines at the end of it by
```
sudo gedit /etc/fstab
``` and saving it.

Copy and paste this into the end of your /etc/fstab
```
/dev/hda1 /home/khirad/c_drive ntfs defaults 0 0
/dev/hda5 /home/khirad/d_drive ntfs defaults 0 0
```

---


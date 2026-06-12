---
title: "New to Kubuntu / Hard drive not detected"
date: 2007-07-31
forum: Absolute Beginner Talk
---

### Post by Brightbelt on 2007-07-31
Hi -
I'm trying Kubuntu for the first time but I do have a fair amount of experience Ubuntu/Gnome. 

My main data/documents drive is my 2nd internal drive which is a swappable-bay hard drive in my HP Pavilion. So it is internal (albeit easily removable) and Ubuntu never had any problem detecting it. Mandriva had no problems detecting it either.

It is an NTFS drive and I've installed and double-checked the NTFS Configuration Tool in Kubuntu, so I don't know what's missing or why it's not showing up. 

I appreciate any help or assistance on this matter,...

Many Thanks, Frank B.

---

### Post by sonofusion82 on 2007-07-31
i m using kubuntu. i also have similar problems for my external USB hard disk which has 3 partitions: 1 NTFS, 2 FAT32. kubuntu will automatically mount the FAT32 partitions but not the NTFS partitions. i have to manuallly mount using command line like:
sudo mount -t auto -o umask=000 [device] [mount_point]

---

### Post by Brightbelt on 2007-07-31
Thanks for the reply - I've never done a  mount like that. I'm assuming the device name might be something like sda2 or something....

What would the mount point be, if you could give me an idea what that might look like?

Many Thanks, Frank B.

---

### Post by Brightbelt on 2007-07-31
I've tried the mount using /dev/sdf as the device which seems right after running 
```
sudo fdisk -l
```

But I tried putting the 'Desktop' as the mounting location and boy that was a disaster (files all over my desktop!).

 Where would I mount this and how would I do the code? I've tried 'file:///media/' and I've tried 'media/' as the mount point and the system accepts neither one. What should I set for the mount point?

Anybody?

Many Thanks, Frank B.

---

### Post by Brightbelt on 2007-07-31
I have googled and searched through [http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty) for help on this. 
A lot of the instructions refer to mounting partitions, but this is a second (2nd),  internal swappable-bay HP hard drive I'm trying to mount.

I have posted a few times now.....I do appreciate any help anyone could offer.

Many Thanks, Frank B.

---

### Post by Brightbelt on 2007-07-31
OK guys. Don't say I never figured anything out for myself! Thanks Sonofusion82 for getting me started. I finally stumbled into the right way to mount my 2nd swappable, internal HP hard drive. This is what worked for me here in Kubuntu:

```
sudo mount -t ntfs-3g /dev/sdb5 /media
```

I've logged out and back in to make sure the mount was right and I think this mounts it correctly. 

'**-t**' is a setting that refers to standard mounting. 
'**ntfs-3g**' refers to the file system.( I finally saw "File System: ntfs-3g" stated somewhere in a window and then realized why 'ntfs' alone wasn't referring to the file system correctly.That was why I kept getting errors.)
**/dev/sdb5** refers to the device name. You can find this by running 

```
sudo fdisk -l
```

and '**/media**' refers to the mount point. 

 If I hit any snags on this I'll update this thread. Thanks and I hope this breakdown helps others on this.

Many Thanks, Frank B.

---

### Post by Brightbelt on 2007-07-31
Ok, some snags here. Not necessarily with a failure to mount. However, I do ALSO have a USB 2.0 external hard drive and it seems that if I try to mount that at the same time as my internal drive, my internal drive gets usurped and overtaken by the external drive.

The 2 different icons are there and they even show their correct device names when I hover my cursor over them. But each one opens the external hard drive only. 

Btw, I adopted Sonofusion's code for mounting the external drive since I think if memory serves, that is what he had. 

I'm talking to myself a lot here folks, so anytime anyone wants to chime in, chime away.

Thanks, Frank B.

---

### Post by meierfra on 2007-07-31
post the output of
```

sudo fdisk -l

```
and 
```
 sudo gedit /etc/fstab 
```
so that we can see what is going on.

---

### Post by Brightbelt on 2007-07-31
Ok Thanks, Here's what I get when I run: sudo fdisk -l:

```

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       31387   237281848+   7  HPFS/NTFS
/dev/sda2           31387       31997     4606976+   f  W95 Ext'd (LBA)
/dev/sda3           31997       40123    61438976   83  Linux
/dev/sda4           40124       41345     9238320    c  W95 FAT32 (LBA)
/dev/sda5           31387       31997     4606976   82  Linux swap / Solaris

Disk /dev/sdb: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2       36481   293025600    f  W95 Ext'd (LBA)
/dev/sdb5               2       36481   293025568+   7  HPFS/NTFS

Disk /dev/sdc: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       24793   199146496    7  HPFS/NTFS
brightbelt@brightbelt-desktop:~$                                   
```

Here's the second one:

```
brightbelt@brightbelt-desktop:~$ sudo gedit /etc/fstab
sudo: gedit: command not found
brightbelt@brightbelt-desktop:~$    
```

Thanks for your help, ....Frank B.

---

### Post by meierfra on 2007-07-31
> "sudo: gedit: command not found

Replace "gedit" by your favorite editor (What flavor of Ubuntu to you use? Xubuntu? )

---

### Post by meierfra on 2007-07-31
Sorry, I must have been sleeping. You clearly announced that you are using Kubuntu. So 

```
kdesu kate /etc/fstab
```

should work.

---

### Post by Brightbelt on 2007-07-31
Read my title: Kubuntu
:)
Thanks, Frank B.

---

### Post by Brightbelt on 2007-07-31
OK, I got your second post, sorry. Here it is:

```
# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda3 :
UUID=bbb8ed10-a8a9-4f65-ba3a-595f23da4e5c / ext3 nouser,defaults,errors=remount-ro,atime,auto,rw,dev,exec,suid 0 1
# Entry for /dev/sda4 :
UUID=627E-79C0 /media/sda4 vfat defaults,utf8,umask=007,uid=0,gid=46,auto,rw,nouser 0 1
# Entry for /dev/sda1 :
UUID=A0D01A87D01A6436 /windows ntfs-3g defaults,locale=en_US.UTF-8 0 1
# Entry for /dev/sda5 :
UUID=ca33ca4f-52f8-4f7c-b045-14b1047e4ea8 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,atime,noauto,rw,dev,exec,suid 0 0
/dev/hd
a /media/cdrom1 udf,iso9660 user,atime,noauto,rw,dev,exec,suid 0 0
/dev/sdf5 <mount\040point> auto nouser,noauto,atime,rw,nodev,noexec,nosuid 0 0

```

Thanks again for helping, Frank B.

---

### Post by meierfra on 2007-07-31
I don't now why, but is seems that  "NTFS Configuration Tool" didn't do its  job.

I will show you how to fix it via the command line. 

Just to make sure: you are trying to have read and write access to your  203G hard drive with a single NFTS partition?

Also where would you like to mount this partition? should be a folder like /media/name_of_your_choice.

---

### Post by Brightbelt on 2007-07-31
There's the internal, 2nd hard drive - /dev/sdb5 I think is the name - which is 278 (300) GB so I'd like to write and  save/copy to that etc, as well as 203 GB drive - /dev/sdg1 is the name I think.

And /media/name is just fine for the mount location, as long as I can access them on the Desktop and things don't get confused.

Many Thanks for your continued help,...Frank B.

---

### Post by Brightbelt on 2007-07-31
BTW, it seems that the device name for my external Usb 2.0 hard drive changes every time I restart or re-log on. For example, when I first did the 'sudo fdisk -l', I got 'sdg1' for that drive. Now I'm getting 
'sdc1'.

Am I wrong or missing something?

Many Thanks, Frank B.

---

### Post by Brightbelt on 2007-07-31
OK, maybe I'm going crazy, but now I can't get it to change the device name no matter what I do. 

Maybe mounting it incorrectly before resulted in the system renaming it. 

:confused:Oh well. 

Many Thanks for helping, ...Frank B.

---

### Post by meierfra on 2007-07-31
First move to the folder /etc

```
  cd /etc 
```

To be save  backup the file fstab

```
sudo cp fstab fstab_backup
```

Open "fstab" with writing permission:

```
 kdesu  kate fstab
```


Add these two lines at the end of the file:

/dev/sdb5   /media/data1 ntfs-3g defaults,locale=en_US.UTF-8 0 1

/dev/sdc1  /media/data2  ntfs-3g defaults,locale=en_US.UTF-8 0 1

Save the file.

We still need to create to  the two folders we used in "fstab"

```
 
cd  /media

sudo mkdir data1

sudo mkdir data2

```

You can  replace data1 and data2 by anything  of your choice. 

Reboot your computer. You should able to access your  file by going to /media/data1 and /media/data2. I'm not sure whether data1 and data2 will appear on your desktop, but we can worry about that later.

---

### Post by meierfra on 2007-07-31
I didn't read your last two post before posting my message. Follow my directions, but we might have to do some tweaking to get the USB drive working.

---

### Post by meierfra on 2007-07-31
I did some googeling and it seems, that for the usb drive all you have to do is install "pmount" and "ntfs-3g" and the drive should mount itself with read and write permissions.

So my instructions should work for your internal drive. But I'm not sure about the "usb drive". 
Maybe its better to leave out the line "dev/sdc1 /media/data2 ntfs-3g defaults,locale=en_US.UTF-8 0 1" in the "fstab".

---

### Post by Brightbelt on 2007-07-31
WOW!! Thanks Meierfra !!!! It worked like a charm !! :)

My USB drive is there as well and they both are remaining separate with data intact.

They were right there on my desktop when I logged in. 

Many Thanks again for all your help,....

Frank B.

---

### Post by meierfra on 2007-08-01
>Many Thanks again for all your help,....

Yor are welcome. 

About the USB drive:  It seems  that my method worked, but there are a couple of problems:  The device  (/dev/sdc ) assigned to the drive might change and  then  the drive won't mount. And the drive must be plugged in during boot up for this to work.

---

### Post by Brightbelt on 2007-08-01
I guess that's what I was seeing before when the 'name' of the usb device seemed to change on me.

I'll certainly keep my eye on it. 

Again, Many Thanks, ...Frank B.

---


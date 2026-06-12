---
title: "new partition is READ OLNY???"
date: 2007-11-21
forum: Absolute Beginner Talk
---

### Post by natehatewindows on 2007-11-21
I just made a 52 GB ext3 partition to put music and videos on so i can share it in ubuntu and mandriva. i have two  questions:

1) it says it is read only and i dont have permissions to change it, how do i change that so i can copy to and from the partition?

2) how do i make this drive auto mount every time i boot to my desktop?

thanks! :)

---

### Post by Paqman on 2007-11-21
You'll be wanting to add a new line to your /etc/fstab file. It's the **f**ile **s**ystem **tab**le.

[Lots of info about fstab](http://ubuntuforums.org/showthread.php?t=283131)

Make sure you make a backup of fstab before editing it. Otherwise a typo could screw up your whole system.

---

### Post by natehatewindows on 2007-11-21
it seems that is mostly for usb drives.....this is a partition on my main hard drive

---

### Post by kpkeerthi on 2007-11-21
1. How did you mount that partition? 
2. If you did add an entry in /etc/fstab, can you post the content of it? 
3. Also, post the output of **sudo fdisk -l** and let us know which partition you want to mount.

---

### Post by natehatewindows on 2007-11-21
it mounted right after i made it with gparted on ubuntu, i have not changed fstab as im still not sure what to put in the file.

here is my fdisk:

home@home-laptop:~$ sudo fdisk -l
[sudo] password for home:

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xeef6b203

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        3847        6457    20972857+  83  Linux
/dev/sda2               1        3846    30892963+   5  Extended
/dev/sda3            7732       14593    55119015   83  Linux
/dev/sda4            6458        7731    10233405   83  Linux
/dev/sda5               1        1041     8361769+  83  Linux
/dev/sda6            1042        3597    20531038+  83  Linux
/dev/sda7            3598        3846     2000061   82  Linux swap / Solaris

Partition table entries are not in disk order

/dev/sda3 is what im wanting to do this with...

thanks!

---

### Post by natehatewindows on 2007-11-21
here is gparted

---

### Post by natehatewindows on 2007-11-21
also i dont want my sda2 to mount anymore, windows used to be here but now it is an extended patition that mandriva is one, can i just delete the line in red to make this not mount?

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4
UUID=27c96fda-9808-4018-a7cf-737a53434618 /               ext3    defaults,errors=remount-ro 0       1
[COLOR="Red"]# /dev/sda2
UUID=BC0816BF0816791A /media/sda2     ntfs    defaults,umask=007,gid=46 0       1[/COLOR]
# /dev/sda7
UUID=e0c6a6ab-e798-4e88-91ae-798adb4556f9 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/sda1       /home    ext3     nodev,nosuid  0  2

---

### Post by kpkeerthi on 2007-11-21
First we create a folder where we could mount the partition
```

sudo mkdir /media/music

```

Add the below line in your /etc/fstab
```

/dev/sda3  /media/music  ext3  defaults 0 1

```

**And Reboot.**

**Note: **
1. Mounting a partion in /media/xxx will automatically create a shortcut on your desktop
2. You could have 0 for the last column instead of 1. A '1' will cause fck to periodically check this filesystem. '0' disables it.

---

### Post by kpkeerthi on 2007-11-21
> **natehatewindows said:**
> also i dont want my sda2 to mount anymore, windows used to be here but now it is an extended patition that mandriva is one, can i just delete the line in red to make this not mount?


Yes. You can just delete the line if you do not want it mounted. **As always make a backup of the file just incase you want to revert back easily**

---

### Post by natehatewindows on 2007-11-21
ok i made the changes to fstab and it worked well but stil wont let me move anything to the disk. how do i get permisson?

---

### Post by kpkeerthi on 2007-11-21
Can you post the output of 
```

ls -ld /media/music

```

(or whatever folder you mounted it to)

---

### Post by natehatewindows on 2007-11-21
home@home-laptop:~$ ls -l /media/storage
total 22548
-rwxrwxrwx 1 home home 23042785 2007-11-15 17:01 GoogleEarthLinux.bin
drwx------ 2 root root    16384 2007-11-21 10:13 lost+found
home@home-laptop:~$ 


i just did 

```
 sudo chmod a+rw /media/storage
```

now i can move file there but cant delete them.....

---

### Post by natehatewindows on 2007-11-21
thanks a lot for the help by the way :)

---

### Post by kpkeerthi on 2007-11-21
Change you fstab as below and reboot.
```

/dev/sda3  /media/music  ext3  defaults**,umask=000** 0 1

```

---

### Post by kpkeerthi on 2007-11-21
The other option is to make 'yourself' the owner of /media/storage
```

chown -R home:home /media/storage

```

I personally prefer the former so I can have all my system users use the storage folder. I would also optionally set the 'sticky' bit for additional safety.

---

### Post by natehatewindows on 2007-11-21
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4
UUID=27c96fda-9808-4018-a7cf-737a53434618 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda7
UUID=e0c6a6ab-e798-4e88-91ae-798adb4556f9 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/sda1       /home    ext3     nodev,nosuid  0  2
/dev/sda3  /media/storage  ext3  defaults,umask=000 0 1

with this it does not mount at all.

---

### Post by kpkeerthi on 2007-11-21
Oops. My mistake. You should remove defaults (since now you are now setting umask explicitly). So it should be
```

/dev/sda3 /media/storage ext3 umask=000 0 1

```

---

### Post by natehatewindows on 2007-11-21
with that it still does not mount,

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4
UUID=27c96fda-9808-4018-a7cf-737a53434618 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda7
UUID=e0c6a6ab-e798-4e88-91ae-798adb4556f9 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/sda1       /home    ext3     nodev,nosuid  0  2
/dev/sda3 /media/storage ext3 umask=000 0 1

---

### Post by natehatewindows on 2007-11-21
could it be something with the command i ran:

sudo chmod a+rw /media/storage

????

---

### Post by natehatewindows on 2007-11-21
ok well i put it back to defaults and now it works great. I hate to ask this here but if i ask on the mandriva forums it will take 100 days to get a reply (ubuntu forums is so much better!).

I did this in mandriva

```
mkdir /media/storage
```

and then out the same entry as i did in ubuntu in the fstab. I can go to /media and clikc the storage folder i created and it shows the partition (says in has 50 some GB free). but it wont mount on my desktop...does anyone know how to make this have a link to my desktop in mandriva? i guess i was told taht anyhting in /media automatically puts a link on the desktop in ubuntu. and i need the same in mandriva..

thanks and sorry for the mandriva talk on ubuntu forums :)

---


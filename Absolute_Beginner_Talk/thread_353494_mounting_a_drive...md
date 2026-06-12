---
title: "mounting a drive.."
date: 2007-02-04
forum: Absolute Beginner Talk
---

### Post by rabid9797 on 2007-02-04
the is the first time ive had to do this.... >.>

its set as as slave, and shows up in gparted as hdb, but i don't know how to mount it and its not showing up under media. help?

---

### Post by taurus on 2007-02-04
What's the output of this command from a terminal?

```
sudo fdisk -l
```

---

### Post by STREETURCHINE on 2007-02-04
hi 
 
        ```
gksudo gedit /etc/fstab
```

and put in 

        ```
/dev/hdb3  /media/shared   ext3   defaults  0  1
```

save and make a new mount point

        ```
sudo mkdir /media/shared
```

         ```
sudo mount -a
```

          ```
sudo chmod -R 777 /media/shared
```   

           ```
df -h
```

i am assuming you are trying to mount ubuntu
you will then find it in media /shared

---

### Post by rabid9797 on 2007-02-04
```
Disk /dev/hda: 30.0 GB, 30020272128 bytes
255 heads, 63 sectors/track, 3649 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3497    28089621   83  Linux
/dev/hda2            3498        3649     1220940    5  Extended
/dev/hda5            3498        3649     1220908+  82  Linux swap / Solaris

Disk /dev/hdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       27403   220114566   83  Linux
/dev/hdb2           30252       30401     1204875   82  Linux swap / Solaris
/dev/hdb3           27404       30251    22876560   83  Linux

Partition table entries are not in disk order
```

---

### Post by rabid9797 on 2007-02-04
> **STREETURCHINE said:**
> 
i am assuming you are trying to mount ubuntu
you will then find it in media /shared


im actually looking to mount one ext3 partition and one ntfs partition.

---

### Post by autocrosser on 2007-02-04
Two Questions:
1. In Gparted, how is the drive formatted?
2. have you ever edited your /etc/fstab file?

Let's say the drive is formatted as EXT3

in a terminal:
sudo gedit /etc/fstab 

you will open text editor with sudo--you will need to add a line that looks like this:

/dev/hdb1        /mnt/"your name here"       ext3         defaults                  0       0

you can use /media/"your name here" instead.
check your work & save the file. then do:

sudo mkdir /mnt/"your name here"

then you can restart your X server or reboot.

To mount a windoze formatted drive, you need to follow the information about fuse.

---

### Post by taurus on 2007-02-04
> **rabid9797 said:**
> im actually looking to mount one ext3 partition and one ntfs partition.

There are no ntfs partition from the output.  

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

### Post by rabid9797 on 2007-02-04
> **taurus said:**
> There are not ntfs partition from the output.

[img]http://xs512.xs.to/xs512/07061/gparted.png[/img]

im confused :(

---

### Post by taurus on 2007-02-04
Try this little test.

```
sudo mkdir /media/hdb1
sudo mount -t ext3 /dev/hdb1 /media/hdb1
```
Did you get any error message from the last command about wrong filesystem?

---

### Post by rabid9797 on 2007-02-04
```

sudo mount -t ext3 /dev/hdb1 /media/hdb1
mount: wrong fs type, bad option, bad superblock on /dev/hdb1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


```

---

### Post by taurus on 2007-02-04
Now try

```

sudo mount -t ntfs /dev/hdb1 /media/hdb1 -o nls=utf8,umask=0222

```

---

### Post by rabid9797 on 2007-02-04
awsome! that got it :) 

now what would i do for hdb2?

EDIT: oh, and am i going to have to do that command everytime i start ubuntu or is it permanently mounted?

---

### Post by taurus on 2007-02-04
I am going to show you how to add three little lines in /etc/fstab so just give me a few seconds.

```
gksudo gedit /etc/fstab
```
Add these three lines to the end of it.

```

/dev/hdb1   /media/hdb1   ntfs   nls=utf8,umask=0222   0   0
/dev/hdb2   none    swap  sw   0   0
/dev/hdb3   /media/hdb3   ext3   defaults   0   1

```
Save it.  Now, create a new mount point for the third partition.

```
sudo mkdir /media/hdb3
```
Reboot.

---

### Post by rabid9797 on 2007-02-04
thanks alot, rebooting now to see if it worked.

---

### Post by rabid9797 on 2007-02-04
success!

---

### Post by txhellkat138 on 2007-05-16
Im kinda having a similar issue. I just installed ubuntu server on a dell poweredge 1900 and it recognizes the 250gb scsi master drive but I cant access the 750gb slave drive at all I tried every thing I have found as A post and it just doesnt wanna touch it it has no info on the the 750gb drive its just an empty drive. WHen I do fdisk -l its listed as /dev/sdb no partitions and I tried ading it to the /etc/fstab as /dev/sdb   /media/shared    defaults   0 1
and I made the proper directory but still a no go any suggestions?

EDIT: Ok so i did everything you guys said right but like an idiot I forgot to format the drive lol

---


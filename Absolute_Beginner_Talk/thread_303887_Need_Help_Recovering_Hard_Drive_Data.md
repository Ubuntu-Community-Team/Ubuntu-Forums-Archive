---
title: "Need Help Recovering Hard Drive Data"
date: 2006-11-21
forum: Absolute Beginner Talk
---

### Post by OBnascar on 2006-11-21
My Kubuntu Dapper system files (hdb1) crashed. I am trying to recover my important data files (hdb3), I used Knoppix 5.0 Live CD and drilled down to my Kubuntu storage partition and it shows it empty. I have Ubuntu that I am using now (hda1) and I can not access hda3 or hdb3 either. In fact I can not see or access hda1 (ubuntu installed, hda3 (storage), hdb1 (kubuntu installed, and hdb3 (storage)

When I first installed Ubuntu and Kubuntu, both distros did not show any media from the file manager. So I had to manually do the following:

sudo mkdir /media/hdb1 (and hdb3, hda1, hda3)
sudo mount -t file_system /dev/hdb* /mnt

then they showed up in the media directory in a file manager, but all showed they were empty, which of course is not possible. I think my /ect/fstab is bad.

```
obnascar@emachines1:~$ sudo fdisk -l
Password:

Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2295    18434556   83  Linux
/dev/hda2            4665        4865     1614532+   5  Extended
/dev/hda3            2296        4664    19028992+  83  Linux
/dev/hda5            4665        4865     1614501   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/hdb: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        2550    20482843+  83  Linux
/dev/hdb2            6998        7297     2409750    5  Extended
/dev/hdb3            2551        6997    35720527+  83  Linux
/dev/hdb5            6998        7297     2409718+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sda: 259 MB, 259522560 bytes
65 heads, 32 sectors/track, 243 cylinders
Units = cylinders of 2080 * 512 = 1064960 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         244      253424    4  FAT16 <32M
Partition 1 has different physical/logical endings:
     phys=(249, 64, 32) logical=(243, 44, 32)
```

```
obnascar@emachines1:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
```


This is copied directly from /etc/fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
```
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
```
As you can see, hda3 and hdb3 are missing in the fstab, and even though hda1 and hdb1 are shown in the fstab, they do not show up in the /media directory. I also have a external CD-RW/DVD-RW drive that does not show up either in fstab or in the /media directory. This is way over my head that is why I am posting it in the "absolute beginners"

Even though I have provided lots of info in this thread, I may be missing info that is still needed, so please let me know.

Any comments, suggestions or opinions are welcome....

best regards,
obnascar

---

### Post by bodhi.zazen on 2006-11-21
So many partitions, so little time.

My head is spinning....

Let's go through an easy solution using hdb1 as an example ....

First your mount command is off....

Should be;```
sudo mount /dev/hdb1 /media/hdb1
```to match your sudo mkdir /media/hdb1
(you do not need to specify the file system type but you may if it makes you happy:```
sudo mount -t file_system /dev/hdb1 /media/hdb1
``` 

One of your drives may be mounted at /mnt ?



Second, try pmount. pmount will mount a drive in /media even if the drive is not listed in fstab.```
pmount /dev/hdb1 sdb1
```

Note: yes, just "hdb1" you do not need to use the full path (ie no need for /media/hdb1).

pmount may not like that your mount point /media/hdb1 already exists, so either delete /media/hdb1 or use mount.

sudo rm -r /media/hdb1
pmount /dev/hdb1 hdb1

OR

```
sudo mount /dev/hdb1 /media/hdb1
```



After you mount hdb1 you can change the permissions if you like:
```
sudo chmod 777 /media/hdb1
```Or access the data as root.




Last fstab. Nothing is wrong with this except not all your partitions were
recognized and added to the file. You can add a line if you like, but there is no need.

> /dev/hdb1 /media/hdb1 auto user 0 0

now you can mount hdb1 without sudo.




HTH



8)

---

### Post by OBnascar on 2006-11-21
bodhi.zazen, thank you for your reply....and yes, that was a mass of info and problems, I agree.

I tried your step by step instructions and when I look at hdb1 in my file manager, it still shows nothing there. Of course in that partition there is a whole OS that resides there. All of the other three of my partitions still show empty also, even for hda1 which I have ubuntu on that I am using as I am typing. 

I am by no means an expert, but I have never experience this before where the content of my partitions are invisable. And they were that way using either ubuntu or kubuntu. I am scratching my head wondering what is going on. I have used over 10 Linux distros and one other time I had to manually mount a partition and then I could see and access it, that was no big deal. 

What has happened to kubuntu and ubuntu ? I have used these distros in the past with no problems, even on this same computer.

Any other idea's ? (I hope, I hope)

cheers,
obnascar

---

### Post by bodhi.zazen on 2006-11-21
were you able to mount without errors ?

If so, please post the output of:

cat /etc/mtab

and

ls -l /media

What file manager ?

---

### Post by OBnascar on 2006-11-21
> **bodhi.zazen said:**
> were you able to mount without errors ?

no..."your mount point /media/hdb1 already exists"

> If so, please post the output of:cat and ls -l /media/etc/mtab
```
obnascar@emachines1:~$ sudo cat /etc/mtab
Password:
/dev/hda1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw 0 0
/sys /sys sysfs rw 0 0
varrun /var/run tmpfs rw 0 0
varlock /var/lock tmpfs rw 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
devshm /dev/shm tmpfs rw 0 0
lrm /lib/modules/2.6.15-27-386/volatile tmpfs rw 0 0
/dev/hdb1 /media/hdb1 ext3 rw,noexec,nosuid,nodev 0 0
/dev/sda1 /media/USB\040DISK vfat rw,nosuid,nodev,quiet,shortname=mixed,uid=1000,gid=1000,umask=077,iocharset=utf8 0 0
```

```
obnascar@emachines1:~$ sudo ls -l /media
total 36
lrwxrwxrwx 1 root   root       6 2006-11-19 09:12 cdrom -> cdrom0
drwxr-xr-x 2 root   root    4096 2006-11-19 09:12 cdrom0
drwxr-xr-x 2 root   root    4096 2006-11-20 20:19 hda1
drwxr-xr-x 2 root   root    4096 2006-11-20 20:23 hda3
drwxrwxrwx 2 jerryo jerryo  4096 2006-11-21 00:09 hdb1
drwxr-xr-x 2 root   root    4096 2006-11-20 20:17 hdb3
drwx------ 6 jerryo jerryo 16384 1969-12-31 19:00 USB DISK
```

> What file manager ?
Nautilus and Krusader

---

### Post by OBnascar on 2006-11-21
I ran Gparted and that does confirm the proper space is being used in hda1, hdb1 and hdb3. 

hda3 storage partition does not have any used space. All of these is correct.

---

### Post by bodhi.zazen on 2006-11-21
One at a time then.

From etc/mtab, hdb1 is mounted:> /dev/hdb1 /media/hdb1 ext3 rw,noexec,nosuid,nodev 0 0

What then is the output of:```
sudo ls -la /media/hdb1
```That is a small "L"....

==========================================================

For hdb2 and hdb3:```
sudo mkdir /media/hdb2

sudo mount /dev/hdb2 /media/hdb2
sudo mount /dev/hdb3 /media/hdb3

sudo ls -la /media/hdb2
sudo ls -la /media/hdb3
```

---

### Post by OBnascar on 2006-11-21
```
obnascar@emachines1:~$ sudo ls -la /media/hdb1
Password:
total 8
drwxrwxrwx 2 jerryo jerryo 4096 2006-11-21 00:09 .
drwxr-xr-x 9 root   root   4096 2006-11-21 10:38 ..
```

```
obnascar@emachines1:~$ sudo ls -la /media/hdb2
total 8
drwxr-xr-x 2 root root 4096 2006-11-21 10:38 .
drwxr-xr-x 9 root root 4096 2006-11-21 10:38 .
```.

```
obnascar@emachines1:~$ sudo ls -la /media/hdb3
total 8
drwxr-xr-x 2 root root 4096 2006-11-20 20:17 .
drwxr-xr-x 9 root root 4096 2006-11-21 10:38 ..
```

---

### Post by bodhi.zazen on 2006-11-21
> **OBnascar said:**
> ```
obnascar@emachines1:~$ sudo ls -la /media/hdb1
Password:
total 8
drwxrwxrwx 2 jerryo jerryo 4096 2006-11-21 00:09 .
drwxr-xr-x 9 root   root   4096 2006-11-21 10:38 ..
```

```
obnascar@emachines1:~$ sudo ls -la /media/hdb2
total 8
drwxr-xr-x 2 root root 4096 2006-11-21 10:38 .
drwxr-xr-x 9 root root 4096 2006-11-21 10:38 .
```.

```
obnascar@emachines1:~$ sudo ls -la /media/hdb3
total 8
drwxr-xr-x 2 root root 4096 2006-11-20 20:17 .
drwxr-xr-x 9 root root 4096 2006-11-21 10:38 ..
```

Looks very grim....

Hate to ask the obvious, but are you **[color=red]SURE**[/color] those drive are mounted? ie are the listed in /etc/mtab (cat /etc/mtab) ?

---

### Post by OBnascar on 2006-11-21
> **bodhi.zazen said:**
> Looks very grim....

Hate to ask the obvious, but are you **[color=red]SURE**[/color] those drive are mounted?
```
[COLOR="DarkGreen"][B]
obnascar@emachines1:~$ sudo mount /dev/hda1
mount: /dev/hda1 already mounted or / busy
mount: according to mtab, /dev/hda1 is already mounted on /

obnascar@emachines1:~$ sudo mount hda3
mount: can't find hda3 in /etc/fstab or /etc/mtab

obnascar@emachines1:~$ sudo mount /dev/hdb1
mount: /dev/hdb1 already mounted or /media/hdb1 busy

obnascar@emachines1:~$ sudo mount /dev/hdb3
mount: can't find /dev/hdb3 in /etc/fstab or /etc/mtab[/B][/COLOR]
```

> ie are the listed in /etc/mtab 
```
[COLOR="DarkGreen"][B]
obnascar@emachines1:~$ sudo cat /etc/mtab
Password:
/dev/hda1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw 0 0
/sys /sys sysfs rw 0 0
varrun /var/run tmpfs rw 0 0
varlock /var/lock tmpfs rw 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
devshm /dev/shm tmpfs rw 0 0
lrm /lib/modules/2.6.15-27-386/volatile tmpfs rw 0 0
/dev/sda1 /media/USB\040DISK vfat rw,nosuid,nodev,quiet,shortname=mixed,uid=1000,gid=1000,umask=077,iocharset=utf8 0 0[/B][/COLOR]
```

---

### Post by bodhi.zazen on 2006-11-21
Do you gaim?

What partition do you need to data recovery? hdb3 ?

The problem is /dev/hdb3 is not mounted yet.

Mount like this:
```
sudo mount /dev/hdb3 /media/hdb3
```
Then```
ls -la /media/hdb3
```

---

### Post by OBnascar on 2006-11-21
> **bodhi.zazen said:**
> Do you gaim?
No....

> What partition do you need to data recovery? hdb3 ?

Yes.....but I can not view or access any of my partitions

> The problem is /dev/hdb3 is not mounted yet. 
Mount like this: sudo mount /dev/hdb3 /media/hdb3

```
[COLOR="DarkGreen"][B]obnascar@emachines1:~$ sudo mount /dev/hdb3 /media/hdb3
mount: /dev/hdb3 already mounted or /media/hdb3 busy
 [/B][/COLOR]
```

> 
Then ls -la /media/hdb3

```
[COLOR="DarkGreen"][B]obnascar@emachines1:~$ ls -la /media/hdb3
total 4
drwxr-xr-x 5 root root  104 2006-11-19 20:59 .
drwxr-xr-x 9 root root 4096 2006-11-21 10:38 ..
drwxr-xr-x 2 root root   80 2006-11-19 21:14 hdb3[/B][/COLOR]
```

---

### Post by bodhi.zazen on 2006-11-21
> **OBnascar said:**
> 

```
[COLOR="DarkGreen"][B]obnascar@emachines1:~$ ls -la /media/hdb3
total 4
drwxr-xr-x 5 root root  104 2006-11-19 20:59 .
drwxr-xr-x 9 root root 4096 2006-11-21 10:38 ..
drwxr-xr-x 2 root root   80 2006-11-19 21:14 hdb3[/B][/COLOR]
```

What is in hdb3?

ls -la /media/hdb3/hdb3

---

### Post by OBnascar on 2006-11-22
This should be the last post I will make on this thread.

I did a bios flash upgrade about a week ago, and I have been having goofy problems such as this every since. Last night was the last "straw"...I lost my Internet connection and at the same time I lost my terminal command line ability, it didn't matter what command I used it always gave me errors. 

I am sorry bodhi.zazen, you spent a lot of effort to help me, I feel bad you spent so much time on this post. I just thought I would let you know why this was all so confusing. I appreciate you trying to help !

best regards,
obnascar

I forgot to add, that computer is going to the computer cemetery !

---

### Post by bodhi.zazen on 2006-11-22
No problem at all. Good luck and com on back if we can be of further assistance !

---


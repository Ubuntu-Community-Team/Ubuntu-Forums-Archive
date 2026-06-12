---
title: "Ok....back to the external HD Q.s"
date: 2006-06-05
forum: Absolute Beginner Talk
---

### Post by CloudyHaze on 2006-06-05
Ok.... After shutting down and bringing my box to work with me, now i have some time to mess with it.

Im still trying to get my external usb hard drive to be seen by ubuntu so that i can back up my files before upgrading to dapper.

Now for the sake of arguement lets start from scratch here.

-I have a Maxtor external Hard Drive(USB) which already contains a mess of files and music that i need to keep.

-I want to add files from my Ubuntu machine to it.

-I plug it in(power and usb), turn it on, then turn on the computer.

-The drive is listed under device manager and under system>admin>disc manager

Under the disk manager it is just listed as Hard Disk
```

Under properties:
Maxtor OneTouch II
 /dev/sda

General Info

Type: Hard Disk
Device: /dev/sda
Speed: n/a

Under partitions: there are no known partitions on this disk
```

I assume it was partition Fat32...... it is 130gb

Any help??

---

### Post by anaconda on 2006-06-05
have you tried to mount it manually?

from terminal:
sudo su
mkdir /sda1
mount /dev/sda1 /sda1

can you now access your USB-drive from /sda1 ??

If the partition was created in windows, it can't be fat32! because windows doesn't allow creating bigger than ~30GB fat32 partitions. (exept Win98)  Then it is probably ntfs partition...

It is wiser to use ext3 partitions and install 
[http://www.fs-driver.org/](http://www.fs-driver.org/)
to windows (if possible, (it needs admin rights)) so that windows can access ext3 partitions.  I haven't had any problems using those...

---

### Post by CloudyHaze on 2006-06-05
Ok....

heres what i get trying to manual mount

i type(after sudo su and in root):
```
 mkdir /sda1 
```

ok seems to work?, it goes back to root command prompt

then i trype:
```
 mount /dev/sda1/sda1
```

and it tells me:

```
 mount: can't find /dev/sda1/sda1 in /etc/fstab or /etc/mtab 
```

---

### Post by anaconda on 2006-06-05
the was supposed to be a space between  /dev/sda1  and  /sda1

Try again. (you dont have to create the /sda1 directory again, so you dont have to run the mkdir /sda1  -line (if you didn't delete the sda1-directory))

---

### Post by CloudyHaze on 2006-06-05
Ok... bear with me :)

ok this time with the space

```
 mount /dev/sda1 /sda1
```

and get:
```
mount: you must specify the filesystem type
```

---

### Post by anaconda on 2006-06-05
if it is fat32
mount -t vfat /dev/sda1 /sda1

if it is ntfs
mount -t ntfs /dev/sda1 /sda1

That should mount the first partition of your external disk. if it has several partitions the next is sda2, sda3 etc.. you can mount them the same way than the first.

But I fear it wont work, because specifying that partition is fat32 or ntfs shouldn't be necessary.. Try it anyway.

---

### Post by CloudyHaze on 2006-06-05
```
mount: special device /dev/sda1 does not exist
```

---

### Post by CloudyHaze on 2006-06-05
OMG!  I must be the biggest ****-up in the history of.......well ok :)


 It seems I totally forgot that i had the security function turned on for the HDD!!!

So i moved it to my windows box....and plugged it.....then Disabled security......

Move back to linux box.....and Boom! it pops right up on the desktop!!! yippy!!!!


Thanks for your help though :D

---


---
title: "2nd hard dive issue"
date: 2007-02-03
forum: Absolute Beginner Talk
---

### Post by greggsbluer6 on 2007-02-03
I am completely new to Ubuntu and i am having a bit of an issue. I have a slightly older system 1GHz AMD 1.5 GIG of ram and two hard drives in the system. During install I chose to have everything installed on the first drive (80 GIG) and nothing on the second drive (300gig). Both drives are IDE, the 80G is master and the 300G is the slave. 

I now what to have the second drive mount automatically when I boot. I had a look at the post below and as my issue is slightly different i created this new post. 

Here is the current output of df -l

gregg@gregg-desktop:~$ df -l
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hda1             73774880   2126188  67901132   4% /
varrun                  777928        80    777848   1% /var/run
varlock                 777928         0    777928   0% /var/lock
procbususb               10240       136     10104   2% /proc/bus/usb
udev                     10240       136     10104   2% /dev
devshm                  777928         0    777928   0% /dev/shm
tmpfs                   777928     17580    760348   3% /lib/modules/2.6.17-10-generic/volatile

As you can see, the second hard drive doesn't show up at all. Then I went and got Gparted and if i select it from the top right corner I can see and format the drive but how do i mount it and have it mount every time I boot?

Thanks in advance!

---

### Post by taurus on 2007-02-03
You need to edit /etc/fstab to add an entry for your second harddrive.

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by greggsbluer6 on 2007-02-03
Sorry I should have been more clear, /dev/hda2 does not exist to add to /etc/fstab. thats what i need to get to show up. Maybe I am still stuck in my windows world here but doesn't the drive have to be known somewhere before you can add it to /etc/fstab?

Sorry about the misunderstanding. 

Gregg

---

### Post by taurus on 2007-02-03
Can you post the output of these two commands here?

```
sudo fdisk -l
cat /etc/fstab
```

p.s.  If you have only one partiton on a harddrive, then it would be known as /dev/hdb1 (first partition of second--slave--drive).

---

### Post by ieee488 on 2007-02-03
System -> Administration -> Disks Manager

you should see your two hard drives along with CD drive, etc on the left hand side

Click on the icon for the 2nd HD. 

Click on the Partitions tab on the right hand side. Click on the Enable button.

with Ubuntu 6.06, my NTFS drives are mounted automatically. I did not have to edit /etc/ftab

---

### Post by greggsbluer6 on 2007-02-03
gregg@gregg-desktop:~$ sudo fdisk -l
Password:

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9331    74951226   83  Linux
/dev/hda2            9332        9729     3196935    5  Extended
/dev/hda5            9332        9729     3196903+  82  Linux swap / Solaris

Disk /dev/hdb: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       36481   293033601   83  Linux


and 

gregg@gregg-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=1c612ed1-413f-460a-bd39-c9d5cb36ec9d /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=6cc9e595-c4b6-4ce8-9f18-946b569b10a2 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by greggsbluer6 on 2007-02-03
I am also using 6.10 and there is no " 	System -> Administration -> Disks Manager"

---

### Post by taurus on 2007-02-03
```
gksudo gedit /etc/fstab
```
and add this line to the end of it.

```
/dev/hdb1   /media/hdb1   ext3   defaults   0   1
```
Save it.  Then, create a new mount point and mount it.

```
sudo mkdir /media/hdb1
sudo mount -a
df -h
```

---

### Post by ieee488 on 2007-02-03
Unless, I'm mistaken, you should be able to use your 2nd HD without mounting etc.
It says it is Linux.

---

### Post by greggsbluer6 on 2007-02-03
AWESOME! Now this works great for me while I am sitting at the keyboard but , what about accessing this remotely with SSH? will I have to mount the drive to access it?

---

### Post by taurus on 2007-02-03
Nope.  /dev/hdb1 will be mounted to /media/hdb1 everytime you turn your Ubuntu on.  If you want to write (delete) to it without using sudo, then you need to change the ownership of /media/hdb1 to you, gregg.

```
sudo chown -R gregg:gregg /media/hdb1
ls -la /media
```

---

### Post by borris.morris on 2007-02-03
Nope, it will work anywhere that the first drive is working. If it works at one place, it will work at all the other places too.

---

### Post by greggsbluer6 on 2007-02-03
Thank you very much for you assistance! ):P

---

### Post by borris.morris on 2007-02-06
no prob. although i didn't do much.

---


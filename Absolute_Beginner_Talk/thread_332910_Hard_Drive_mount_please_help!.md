---
title: "Hard Drive mount please help!"
date: 2007-01-06
forum: Absolute Beginner Talk
---

### Post by Chrisie on 2007-01-06
[SIZE="3"][/SIZE]Wondering if anyone can help me. Im new, VERY new but I really want to get into using ubunu and throw away windows.

Okay here my problem.

Can not see any of my hard drives at all only "filesystem" in "computer". 

Ive found out how to access Terminal, then sudo fdisk -l and I get...

Disk /dev/sda: 250.0 GB, 250059350016 bytes
240 heads, 63 sectors/track, 32301 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         967     7310488+   c  W95 FAT32 (LBA)
/dev/sda2   *         968       32300   236877480    7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       18707   150263946   83  Linux
/dev/sdb2           18708       19457     6024375    5  Extended
/dev/sdb5           18708       19457     6024343+  82  Linux swap / Solaris

The 250GB hd is my windows ntfs drive and the 160GB is now my Ubuntu,

I want to able to access the windows(250GB sda2) drive but I cant even access the 160GB

Please can anyone help me. Help me get shot of windows before I go mad,

Thank you.

Chrisie

P.S,
       I so new you will have to explain very clearly :) ](*,) :confused:

---

### Post by taurus on 2007-01-06
Okay, see if I can get this to work.  Open a terminal, Applications -> Accessories -> Terminal, so you can edit your /etc/fstab.

```
gksudo gedit /etc/fstab
```
Scroll to the end and add the following two lines to it.

```

/dev/sda1   /media/sda1   vfat   iocharset=utf8,umask=000   0   0
/dev/sda2   /media/sda2   ntfs   nls=utf8,umask=0222   0   0

```
Save the changes.  Then, create two new mount points and mount them.

```
sudo mkdir /media/sda1 /media/sda2
sudo mount -a
df -h
```
Now, you can read and write to /media/sda1 but you can only read to /media/sda2--ntfs filesystem...

And by the way, the second harddrive, /dev/sda, is already mounted because you are using it right now.

---

### Post by Chrisie on 2007-01-06
Now I get

Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1             142G  2.2G  132G   2% /
varrun               1006M   80K 1006M   1% /var/run
varlock              1006M     0 1006M   0% /var/lock
procbususb             10M  200K  9.9M   2% /proc/bus/usb
udev                   10M  200K  9.9M   2% /dev
devshm               1006M     0 1006M   0% /dev/shm
lrm                  1006M   21M  985M   3% /lib/modules/2.6.17-10-generic/volatile
/dev/sda1             7.0G  3.3G  3.7G  47% /media/sda1
/dev/sda2             226G  183G   44G  81% /media/sda2

But I still dont see the drives in "places", "computer"

Also if I type /dev/sda1 into terminal is says "bash: /dev/sda1: Permission denied"

At least im getting somewhere.

Chrisie

---

### Post by taurus on 2007-01-06
```
cd /media/sda1
ls -la
```
Or use nautilus...

---

### Post by Dragon43 on 2007-02-14
Another new user needing help with a second hard drive.

I just want to use the second hard drive as a full mirror backup. I use mobile trays and mirror my Win-98 system about once a week to my second hard drive.  I want to do the same on my "Ubuntu" 6.06 machine.  It **IS** a completely separate machine.  It is connected to my in house net work but none of my machines is dual boot nor do I want that.

So, how to format? ( do in need to?)
How to get 'Ubuntu' to see it and how do I just do a **complete mirror** when I have 'Ubuntu' doing good and want to save it before going on to the next learning phase? 

I unplug the second drive physically from my machines (3, wifes win box, my win box and now the "U" machine) so that mechanical, electrical, virus attacks, or my **messing around** can not mess with it.

Please help.

*I formatted it on my windows machine ???*

My terminal gave me this with ( sudo fdisk -l )

> Password:

Disk /dev/hda: 40.9 GB, 40981118976 bytes
255 heads, 63 sectors/track, 4982 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4842    38893333+  83  Linux
/dev/hda2            4843        4982     1124550    5  Extended
/dev/hda5            4843        4982     1124518+  82  Linux swap / Solaris

Disk /dev/hdb: 8455 MB, 8455200768 bytes
255 heads, 63 sectors/track, 1027 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        1027     8249346    c  W95 FAT32 (LBA)


So, what do I do????

Please use step by step, I have been trying this for only 12 days and I need to be lead by the hand.  I'm 63 years old and only came to computers in 1998.

I started with Win-3.1 and AOHell 3.0.  No MAC experience and no DOS experience.

I am haveing fun with "Ubuntu" and learning a lot but I have to have pictures with lots of words, circles and arrows on the back.
Please help

---

### Post by Dragon43 on 2007-02-15
I was sure someone would see this and help.... Anyone?

---

### Post by Patrick K on 2007-02-15
Opps, I don't really have anything to say.

---

### Post by Dragon43 on 2007-02-15
Bawahahahaha, OK, you got me.

Hope this gets seen soon.

---


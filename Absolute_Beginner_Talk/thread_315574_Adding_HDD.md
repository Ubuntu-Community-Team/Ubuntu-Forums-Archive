---
title: "Adding HDD"
date: 2006-12-09
forum: Absolute Beginner Talk
---

### Post by say592 on 2006-12-09
I need help mounting my HDD thats already installed (not the one ubuntu is running on, my other one, it was formated to run win. xp) As well as how will mount/partition my other HDD when I install it?

---

### Post by lemonsCC on 2006-12-09
Is it still formatted to run win XP?  Do you want win XP on it?  What do you plan on doing with this harddrive?

---

### Post by taurus on 2006-12-09
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by say592 on 2006-12-09
Ok, I want to keep windows on the other hdd, and I want to partition the 160gb I just bought to run vista and have file space to use on xp, linux, and vista. I plan to partition it 120gb/40gb for vista/files

---

### Post by lemonsCC on 2006-12-09
You will want to boot the Ubuntu liveCD and open Gparted.  It will display your 160gb HD.  Right click it and resize it to 120gb.  It should show ~40gb of unallocated space after your 120gb partition.  Right click on the unallocated space and format it to Fat32 (if you want xp, vista, and linux to be able to read and write to this partition.)  Click apply. 

Follow taurus' link from here

---

### Post by say592 on 2006-12-09
ok, maybe its the absolute linux n00b in me, but I get to a certain point on that tutorial taurus linked to, then I go BOOM no clue what I am doing, its the part where you are edditing the file or whatever, I just dont get it..........

---

### Post by taurus on 2006-12-09
Paste the output of this command from a terminal and tell me which partition(s) you want to mount.  Will walk you through it here then...

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by say592 on 2006-12-09
OK i want to mount the hdc one, here is a link to a screenshot: [http://psp-temple.com/smf/index.php?action=dlattach;topic=38.0;id=20;image](http://psp-temple.com/smf/index.php?action=dlattach;topic=38.0;id=20;image)

and if you can/want to, i dont mind using aim or another im client for more instant assistance........

---

### Post by taurus on 2006-12-09
Hey, I can't view it because I don't have login name and password.  So you just have to paste the output here then.  Besides, don't use aim, im, or whatever else...  ;)

---

### Post by lemonsCC on 2006-12-09
say592 you could come to the irc channel...

irc.freenode.net  #ubuntu

I am there now

---

### Post by say592 on 2006-12-09
> **taurus said:**
> Hey, I can't view it because I don't have login name and password.  So you just have to paste the output here then.  Besides, don't use aim, im, or whatever else...  ;)

Ok sorry that that didnt work, and what do you mean about im? o well here is the output:

joshua@joshua-desktop:~$ sudo fdisk -l
Password:

Disk /dev/hdc: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               1           5       40131   de  Dell Utility
/dev/hdc2   *           6        9300    74662087+   7  HPFS/NTFS
/dev/hdc3            9301        9725     3413812+  db  CP/M / CTOS / ...

Disk /dev/hdd: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1        2330    18715693+  83  Linux
/dev/hdd2            2331        2434      835380    5  Extended
/dev/hdd5            2331        2434      835348+  82  Linux swap / Solaris
joshua@joshua-desktop:~$ 


And should I go ahead and drop in the 160gb now, if I do can I partition it easily? (the one I want to mount is the hdc drive, the 80gb one)

---

### Post by taurus on 2006-12-09
What the heck is that "/dev/hdc3 9301 9725 3413812+ db CP/M / CTOS / ..." thing?  Do you want to mount /dev/hdc2?

---

### Post by say592 on 2006-12-09
yes hdc2 is it, and should i add my 160gb now and do it all at once, or would it be easyer to mount it later (and partition it)

---

### Post by taurus on 2006-12-09
Well, it's up to you but in the meantime, here's your /dev/hdc2...

Applications -> Accessories -> Terminal
```
sudo cp /etc/fstab  /etc/fstab.bak <-- make a backup copy
gksudo gedit /etc/fstab
```
Scroll down to the end and add this line to it.

```

/dev/hdc2   /media/hdc2   ntfs   nls=utf8,umask=0222   0   0

```
Save it and now, create a mount point and mount it...

```
sudo mkdir /media/hdc2
sudo mount -a
df -h <-- you should see your /dev/hdc2 on /media/hdc2 from this list...
```

---

### Post by say592 on 2006-12-09
Ok so this is read only right? That should be fine, as I just want to copy it to my 160gb, and in the code, do I run one line hit enter, then the other one, for the mutiline codes?

---

### Post by lemonsCC on 2006-12-09
one line at a time yes.

Read only yes.

---

### Post by say592 on 2006-12-09
OK so I see it on that list, but how do i access it

---

### Post by taurus on 2006-12-09
```
ls -la /media/hdc2
```
or use nautilus and browse to it...

---

### Post by say592 on 2006-12-09
Thanks! Can u check this thread in about 20min incase i have issues with installing my other one.... Oh and how do I partition it? Do I have to use the CD? Or is there a program I can install?

---

### Post by taurus on 2006-12-09
> **say592 said:**
> Thanks! Can u check this thread in about 20min incase i have issues with installing my other one.... Oh and how do I partition it? Do I have to use the CD? Or is there a program I can install?
I can check this one again but won't be until real late tonight since I have to go to work in a few minutes.  If you want to partitions a new drive (which Ubuntu is not on), you can install gparted and use it from Ubuntu directly.  No need to use the LiveCD UNLESS you want to resize Ubuntu...

```
sudo aptitude update
sudo aptitude install gparted
```

---

### Post by say592 on 2006-12-09
Ok, and I will be up till late, so yeah if you will check on it, I mat be able to finish tonight! Thanks!

Dang it! That code gave me an error:

E: Couldn't rebuild package cache
joshua@joshua-desktop:~$ sudo aptitude install gparted
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
joshua@joshua-desktop:~$

---

### Post by say592 on 2006-12-10
Ok so I got the 80gb mounted, and I dropped the 160gb in and formated 45gb in fat32 and here is the read out of my sudo fdisk -l:

joshua@joshua-desktop:~$ sudo fdisk -l

Disk /dev/hdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        5816    46716988+   b  W95 FAT32

Disk /dev/hdc: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               1           5       40131   de  Dell Utility
/dev/hdc2   *           6        9300    74662087+   7  HPFS/NTFS
/dev/hdc3            9301        9725     3413812+  db  CP/M / CTOS / ...

Disk /dev/hdd: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1        2330    18715693+  83  Linux
/dev/hdd2            2331        2434      835380    5  Extended
/dev/hdd5            2331        2434      835348+  82  Linux swap / Solaris
joshua@joshua-desktop:~$ 


Obviously I want to mount the fat32 with about 45gb, now how? I tried to do it how we did earlyer, but that didnt work :( so..... I think I got alot of this down, but what is the string I need to put into the file I eddit?

---

### Post by taurus on 2006-12-10
So you want to mount /dev/hdb1!

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/fstab
```
Scroll down to the end and add this line for it.
```

/dev/hdb1   /media/hdb1   vfat   iocharset=utf8,umask=000  0  0

```
Save it and create a mount point and mount it.
```
sudo mkdir /media/hdb1
sudo mount -a
df -h
```

---

### Post by say592 on 2006-12-10
Thanks, I tried modding the code you gave me for the first one, and I had it looking like this: /dev/hdb1   /media/hdb1   fat32   iocharset=utf8,umask=000  0  0

I was so close! lol well thanks! I think for the rest of my linux life I will know how to mount an hdd lol

---

### Post by taurus on 2006-12-10
> **say592 said:**
> Thanks, I tried modding the code you gave me for the first one, and I had it looking like this: /dev/hdb1   /media/hdb1   fat32   iocharset=utf8,umask=000  0  0

I was so close! lol well thanks! I think for the rest of my linux life I will know how to mount an hdd lol
Glad to hear that you can access all your harddrives now.

---


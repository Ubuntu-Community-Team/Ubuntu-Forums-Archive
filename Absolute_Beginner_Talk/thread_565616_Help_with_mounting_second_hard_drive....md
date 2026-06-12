---
title: "Help with mounting second hard drive..."
date: 2007-10-02
forum: Absolute Beginner Talk
---

### Post by orpat on 2007-10-02
Feisty, Recent install. I have 2 20 gig HD. One is setup correctly, everything works. 

The second is set up with 3 partitions: 2 as Ext 3 , 1  as unallocated. when I mount these partitions, they all come up as mirrors of my main HD. I need to get rid of the mirrors and mount them as storage. I _am not_ doing a dual boot,  I have only 2 programs  to run under XP and I am doing that under an emulator (still playing to see which one I like best).

Thanks in advance

Pat

---

### Post by benerivo on 2007-10-02
What do you mean by mirrors? Do you mean that what is getting mounted is not the 2nd hard drive, but actually the contents of your main hard drive?

---

### Post by orpat on 2007-10-03
Yep. and no matter how I format the drive. it either become unusable or reverts to  being a duplicate. If I format it as EXT3, I can read and write to it for that session, and then at boot something (gimp?) overwrites it and it goes back to being unusable/ copy, I did get it down to one partition instead of 3.
I have created some folders on the second drive and when I re-format they come back...

Pat

---

### Post by taurus on 2007-10-03
Do you mount the second drive by hand or do you mount it through /etc/fstab?

What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by orpat on 2007-10-03
Here you go:



Disk /dev/sda: 27.3 GB, 27373731840 bytes
255 heads, 63 sectors/track, 3328 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1653    13277691   83  Linux
/dev/sda2            3117        3328     1702890    5  Extended
/dev/sda3   *        1654        3116    11751547+  83  Linux
/dev/sda5            3188        3328     1132551   82  Linux swap / Solaris
/dev/sda6            3117        3187      570244+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 20.5 GB, 20547841536 bytes
255 heads, 63 sectors/track, 2498 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        2498    20065153+  83  Linux

---

### Post by taurus on 2007-10-03
I assume /dev/sdb1 is the one you want to mount.

```
sudo mkdir /media/sdb1
sudo mount -t ext3 /dev/sdb1 /media/sdb1
sudo chown -R **orpat**:**orpat** /media/sdb1
(_Assuming_ **orpat** is your login name.  Replace it with the right one, okay...)
ls -la /media/sdb1
```
Now, you should be able to write to /media/sdb1 because you are the owner of it.

---

### Post by orpat on 2007-10-03
Actually I am mounting it through the gnome partion editor.. my MIstake??
I am not yet "learn-ed" in the linux command line stuff. Only been off windows since Sunday. And haven't had to much cmmand line stuff since the days of DOS.

---

### Post by taurus on 2007-10-03
Once you execute those commands from a terminal (Applications -> Accessories -> Terminal), you then should be able to use nautilus to copy files to /media/sdb1 anytime you want.

And if you want to mount /dev/sdb1 each time you boot your machine so you don't have to mount it by hand, then edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and add this line to the end of it.

```
/dev/sdb1   /media/sdb1   ext3   defaults   0   1
```

Save it and reboot.

---

### Post by orpat on 2007-10-03
OK Got it to work. The parameter is  -hR. I had to look in chown help
Will add the  auto-mounting info
Where is the best list of terminal commands??

Thank you so much
Pat

---


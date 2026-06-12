---
title: "[SOLVED] putting /home on its own partition."
date: 2008-02-25
forum: Absolute Beginner Talk
---

### Post by Papa-san on 2008-02-25
I think I messed up during my install...Can this be changed after installation? I have my partitions set. (I think)
Here is fdisk -l:
```
Disk /dev/sda: 20.0 GB, 20003880960 bytes
255 heads, 63 sectors/track, 2432 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc919c919

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         879     7060536   83  Linux
/dev/sda2             880        1729     6827625   83  Linux
/dev/sda3            2331        2432      819315    5  Extended
/dev/sda4   *        1730        2330     4827532+  83  Linux
/dev/sda5            2365        2432      546178+  82  Linux swap / Solaris
/dev/sda6            2331        2364      273042   82  Linux swap / Solaris

Partition table entries are not in disk order
john@john-laptop:~$ 

```
I don't know why there are so many, but that's what I have. What did I do wrong, and can it be fixed? I need my root partition, /home partition, and I guess a swap partition.

---

### Post by taurus on 2008-02-25
Did you install Ubuntu once and then reinstalled Ubuntu again?  That would explain why you have two of everything.

---

### Post by Papa-san on 2008-02-25
I had it (6.06) installed along with winxp. I used gparted to set up another partition using the xp space (getting rid of it). Then I installed 7.10

(Hi taurus!)   :-)

---

### Post by taurus on 2008-02-25
So, looks to me now you have both versions 6.06 and 7.10 on your machine.  If you don't have anything important on your harddrive, use gparted from the LiveCD and delete all the partitions.  Then, create three partitions:  /, /home, & swap and reinstall Gutsy again.  Now, you have a clean and lean machine.

---

### Post by Papa-san on 2008-02-25
OK. So how do I go about doing that? I thought I had done it, and evidently messed it up...

I'm guessing when it asked me if I wanted to save info from my last setup, I should have said no...

So, when I re-install again, do I name the partitions during the initial install? How does one do this?

I know... I know... holdin my hand, again! LOL

Oh, and size-wise, will a 6 gig partition work for / ? Then 500 megs for swap? The rest for /home ?

---

### Post by Papa-san on 2008-02-25
Hmmmm... gparted doesn't want to run from the CD

---

### Post by taurus on 2008-02-25
Boot Gutsy LiveCD.  Then, fire up gparted in System -> Administration and use it to delete all the partitions.  Then, create three new partitions:  /dev/sda1 (6GB), /dev/sda2 (500MB), & /dev/sda3 (whatever left).  Format both /dev/sda1 & /dev/sda3 as ext3 while tag /dev/sda2 as swap.

Once everything is done, close down gparted and click the install icon on the desktop.  Follow instructions on screen until you get to the partition part.  Pick Manual and highlight /dev/sda1 partition and tell the installer to mount it to / (instead of /media/sda1 as you should see).  Then, highlight /dev/sda3 and mount it to /home.  You can format them again if you wish.  No need to do anything with /dev/sda2 since the installer should automatically mounts that as swap.  

Then proceed.

---

### Post by bodhi.zazen on 2008-02-25
Just a "heads up" you probably will not be able to delete all your partitions unless you unmount the swap partitions. Use swapoff :

```
sudo swapoff /dev/sda5
sudo /dev/sda6
```

What happens when you run :

```
gksu gparted
``` in a terminal ?

---

### Post by Papa-san on 2008-02-25
I ran swapoff for both sda5 &6

When I run gksu gparted, the GUI opens and it says "Scanning all devices..." and the orange bar thingy goes back and forth, but nothing happens. It's been doing that for 34 minutes now....
In terminal I just got:
```
Unable to open /dev/fd0 read-write (Read-only file system). /dev/fd0 has been 
opened read-only.
```

---

### Post by bodhi.zazen on 2008-02-25
Yea, that is a bug : [https://bugs.launchpad.net/gparted/+bug/155047](https://bugs.launchpad.net/gparted/+bug/155047)

IMO best advice is to specify you HD :

```
sudo gparted /dev/sda
```

---

### Post by Papa-san on 2008-02-26
Thanks. I managed to get into it and deleted the partitions. I forgot to swapoff again after the re-boot though, so its not reading all my space as sda...

I reported some associated data to the guy working on the bug. 

I was seeing some I/O errors before the live CD would start to boot, and my system would hang there for a couple of minutes also. I sent him the addresses or whatever they are called.

---

### Post by Papa-san on 2008-02-26
OK...
That bug manifested itself three times during my attempts at re-installing: (In case someone searches these forums for the errors I got)

1 - As described before, at initial boot-up with the live CD.```
 [199.876000] I/O Error on device fd0, logical block 0. and 
[237.980000] I/O Error on device fd0, logical block 0.
```

2 - During the attempts to run gparted,

3 - when the installer's partitioner stalled during scanning at 46%.

I did go in to BIOS and disabled the floppy. This laptop has the kind of drive where you have to remove and install the floppy and CD modules in the same bay. Can only use 1 at a time.
So, anyways, I am watching it install now... And it seems to have locked up... 

Anyways, I'll mark this as solved, as I managed to get through the partitioning process.

---


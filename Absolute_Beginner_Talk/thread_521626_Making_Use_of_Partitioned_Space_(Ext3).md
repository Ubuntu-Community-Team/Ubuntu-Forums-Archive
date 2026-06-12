---
title: "Making Use of Partitioned Space (Ext3)"
date: 2007-08-04
forum: Absolute Beginner Talk
---

### Post by babysteps on 2007-08-04
Thanks for this info.  I had just gotten a 250 gig Seagate external hard drive and had searched for ways to format the drive for use with Ubuntu. 

I have the PCLInuxOS live CD and have gotten the DiskDrake to format the drive, but I'm not very sure which choice should be for ubuntu system?  I'm not using it for windows, so should I chose the "journalisted FS"? Or "Ext2"? Or something else?

Also, why does the 250 G show up as 232 G only?

I hope this thread isn't too old to get a reply...

Thanks!

Babysteps

---

### Post by aysiu on 2007-08-04
I would go for Ext3

Read this:
[http://en.wikipedia.org/wiki/Gigabyte#Consumer_confusion](http://en.wikipedia.org/wiki/Gigabyte#Consumer_confusion)

---

### Post by babysteps on 2007-08-06
Thanks Aysiu.  There wasn't a label that said Ext3, but something about "journaled FS" that I chose.  After formatting it the property did turn out to be Ext3.

Also thanks for the link to clear up the "missing" gigs. 

Babysteps

> **aysiu said:**
> I would go for Ext3

Read this:
[http://en.wikipedia.org/wiki/Gigabyte#Consumer_confusion](http://en.wikipedia.org/wiki/Gigabyte#Consumer_confusion)

---

### Post by babysteps on 2007-08-09
> **aysiu said:**
> I would go for Ext3

Read this:
[http://en.wikipedia.org/wiki/Gigabyte#Consumer_confusion](http://en.wikipedia.org/wiki/Gigabyte#Consumer_confusion)

Now that I got the 250 gig hard drive formatted, I see it on the desktop as a "232.2 GB Volume".  I'm not sure if I messed up when   I was formatting it because I had installed ubuntu onto it.  I'm wondering if this is why I cannot write anything unto it?  It complains that I have no permission to see it.  There's only something called "Lost + Found" on it which I know is the installation of ubuntu.  So, here i have 232 GB of space and I can't use it. When I click on Property ->permission, it's all grayed out. with the view number of 755, and the message that I'm not the owner.

What am I doing wrong?

---

### Post by aysiu on 2007-08-09
Try this:
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

### Post by babysteps on 2007-08-09
> **aysiu said:**
> Try this:
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

Thanks Aysiu for the link.  I tried it, but I am stuck on two places:
1)I couldn't get the update because this laptop is still on Breezy. 5.10.  though I figure i didn't need to use gparted because I know the file system is ext 3 from PClinuxOS's formatting.

2) I couldn't get the chown -R (username): (username) /storage to work. my username has a hyphen in it.  Is that the problem?

Another thing I was wondering is whether I should reformat again and get rid of the swap on the 232 GB that has an extra ubuntu installed? Maybe then it can be written to?

Thanks!

Babysteps

---

### Post by aysiu on 2007-08-09
I noticed that you put a space after the colon: > chown -R (username): (username) /storage There shouldn't be a space there. It should be ```
sudo chown -R firstpart-secondpart:firstpart-secondpart /path/to/partition
``` By the way, I think you'll get better help in a devoted thread instead of piggybacking on the DiskDrake tutorial, so I've moved your posts out here.

---

### Post by babysteps on 2007-08-10
> **aysiu said:**
> I noticed that you put a space after the colon:  There shouldn't be a space there. It should be ```
sudo chown -R firstpart-secondpart:firstpart-secondpart /path/to/partition
``` By the way, I think you'll get better help in a devoted thread instead of piggybacking on the DiskDrake tutorial, so I've moved your posts out here.

I had replied last night, but somehow it didn't show up in this thread.

You were absolutely right, before, I had given  it an extra space after the :  and there had the error message.  

Another thing I got an erro message for ("line 6 is bad" it tells me ) I realize was because I was trying to do the same spacing as in the /etc/fstab and I really should just do without extra. 

Anyway, learning here. 

This time when I typed "sudo mount -a" I got a message saying that the /dev/hda5 was already mounted or is busy (?)

Should this external USB drive be hda or sda, by the way?  Is it not possible to use it for more than one computer?  Should I have had it formatted to "supermount"?

Thanks Aysiu!

Babysteps

---

### Post by aysiu on 2007-08-10
I'm not sure. Can you post the output of these commands (copy and paste is fine--leaves less room for error)? ```
sudo fdisk -l
df -h
cat /etc/fstab
```

---

### Post by babysteps on 2007-08-10
> **aysiu said:**
> I'm not sure. Can you post the output of these commands (copy and paste is fine--leaves less room for error)? ```
sudo fdisk -l
df -h
cat /etc/fstab
```

Sure thing. Here's:

sudo fdisk -l


Disk /dev/hda: 20.0 GB, 20003880960 bytes
255 heads, 63 sectors/track, 2432 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2329    18707661   83  Linux
/dev/hda2            2330        2432      827347+   5  Extended
/dev/hda5            2330        2432      827316   82  Linux swap / Solaris


df -h

Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1              18G  9.8G  7.0G  59% /
tmpfs                 189M     0  189M   0% /dev/shm
tmpfs                 189M   13M  176M   7% /lib/modules/2.6.12-10-386/volatile


cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5 /storage ext3 defaults 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd0       /media/dvdrom
/dev/sda /storage ext3 defaults 0 0


Thanks for helping me!

Babysteps

---

### Post by aysiu on 2007-08-11
> **babysteps said:**
> ```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
**/dev/hda5 /storage ext3 defaults 0 0**
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd0       /media/dvdrom
**_/dev/sda /storage ext3 defaults 0 0_**
``` It looks as if you have two devices (/dev/hda1 and /dev/sda) mounted to /storage. That isn't going to work.

I would delete the last line (the one underlined) and then try ```
sudo mount -a
``` afterwards.

---

### Post by babysteps on 2007-08-11
> **aysiu said:**
> It looks as if you have two devices (/dev/hda1 and /dev/sda) mounted to /storage. That isn't going to work.

I would delete the last line (the one underlined) and then try ```
sudo mount -a
``` afterwards.

OK, I got rid of that extra line. Here's what I get:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5 /storage ext3 defaults 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd0       /media/dvdrom


sudo mount -a

mount: /dev/hda5 already mounted or /storage busy
mount: mount point /media/dvdrom does not exist

(I don't have my dvdrom turned on)

Sorry to be so much trouble....

Babysteps

---

### Post by aysiu on 2007-08-11
Maybe comment out that /media/dvdrom line, too. It looks incomplete anyway.

Then reboot your computer. That should take care of the "busy" problem with mounting.

---

### Post by babysteps on 2007-08-18
> **aysiu said:**
> Maybe comment out that /media/dvdrom line, too. It looks incomplete anyway.

Then reboot your computer. That should take care of the "busy" problem with mounting.

sorry, I didn't have much time with the computer for the last week! 
I did reboot but still can't write to the seagate.

I have a dumb question here: Can I use laptop A to format a drive that I want to be able to use with latop B? I'm asking from the point of view that  I was told that the seagate isn't a "portable" drive, but is an external drive. Is It being not a "portable" drive means that it's not one of those usb pendrive that you can plug into any laptop? 

Babysteps

---


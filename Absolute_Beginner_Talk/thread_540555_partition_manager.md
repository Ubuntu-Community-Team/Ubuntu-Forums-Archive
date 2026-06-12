---
title: "partition manager"
date: 2007-09-01
forum: Absolute Beginner Talk
---

### Post by Paches363 on 2007-09-01
I'm trying to get a duel boot rig going with Ubuntu, and I tried using Gnome Partition editor and it wont allow me to resize my partition can anyone offer any Help? Im running on the newest Ubuntu 7.04 I have searched for updates etc. Im kinda a noob but i know some of the general stuff is there something else i should be using?

---

### Post by taurus on 2007-09-01
Are you trying to resize Ubuntu partition so you can install Windows on the new partition?  

If that's the case, you need to do that from the LiveCD since you can't resize the partition while you are using it.

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by Paches363 on 2007-09-01
oh.... lol yeah thats what i am trying to do thanks i never would have thought of that 
Thank you

---

### Post by kellemes on 2007-09-01
> **Paches363 said:**
> oh.... lol yeah thats what i am trying to do thanks i never would have thought of that 
Thank you

I can understand you didn't think of this since I can use Partition Magic on Windows and resize any partition at any time.. GParted isn't that advanced yet..

---

### Post by Paches363 on 2007-09-01
Ok so i got onto my live disk and im in the partition manager and when ive made my changes and hit apply it pops and error wich says.


Check filesystem on /dev/sda1 for errors and (if possible) fix them

e2fsk -f -y -v /dev/sda1

/dev/sda1 is mounted

e2fsk 1.40-WIP (14-Nov-2006)
e2fsk: cannot continue, aborting

What dose that mean and what do i do about it?

---

### Post by taurus on 2007-09-01
What's the outputs of these commands from a terminal?

```
sudo fdisk -l
df -h
```
Otherwise, try to unmount it before you run gparted again.

```
sudo umount /dev/sda1
```

---

### Post by Paches363 on 2007-09-01
When i typed sudo fdisk -l I got 


Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19080   153260068+  83  Linux
/dev/sda2           19081       19457     3028252+   5  Extended
/dev/sda5           19081       19457     3028221   82  Linux swap / Solaris


and When i typed df -h

Filesystem            Size  Used Avail Use% Mounted on
tmpfs                 506M   33M  473M   7% /lib/modules/2.6.20-15-generic/volatile
tmpfs                 506M   33M  473M   7% /lib/modules/2.6.20-15-generic/volatile
varrun                506M   96K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
udev                  506M   84K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
tmpfs                 506M   12K  506M   1% /tmp
/dev/sda1             144G  9.7G  127G   8% /media/disk




And as for the unmounting the drive command i tried it and got the same error, i dont think the Partition editor even lets you mess with the drive if its mounted

---

### Post by taurus on 2007-09-01
Are you using Ubuntu LiveCD or the GParted LiveCD?  I strongly recommend you use GParted LiveCD (from the link in my previous post) since it comes with the latest version of gparted.

---

### Post by Paches363 on 2007-09-01
no i was useing my Ubuntu one ill give the other one a shot

---

### Post by ramjet_1953 on 2007-09-01
Also, it is imperitive that you defragment your Windows partition at least a couple of times before re-partitioning.

Regards,
Roger 8-)

---

### Post by Paches363 on 2007-09-01
Yeah... lol i was actually planning on switching from a vista, XP duel boot to a Ubuntu, Vista duel boot but after i had finished backing up all of my stuff i started defraging and windows crashed, so i went into vista to burn my disk ubuntu disk but it just went into this silly non stop boot cycle of loading half way then restarting. So i just burnt it on XP and then formated the whole damn thing.

---


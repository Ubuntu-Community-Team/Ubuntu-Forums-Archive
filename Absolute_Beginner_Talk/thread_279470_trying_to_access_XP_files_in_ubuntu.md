---
title: "trying to access XP files in ubuntu"
date: 2006-10-18
forum: Absolute Beginner Talk
---

### Post by karinne on 2006-10-18
Hi, 
my second question of the day. I have a lot of work in my documents folder over on the XP ntfs partition. If I am going to work at all in ubuntu, i at least need to be able to read some of these, if not be able to write to and save them (either here in ub. or over there in xp).  but reading is essential. 
So when i go to Disks Manager, I can see the ntfs partition, but when I select 'browse' (which I assumed would lead me to an 'explore' type thing), I get this message: 

"the folder contents cannot be displayed: you do not have the permissions neccesary to view the contents of 'disks-conf -sda1'"

How to fix this? Or, is there another quick easy way to view files from My Documents folder in XP over here in Ubuntu?  
Do i need to reboot, get into XP, and set permissions for specific folders? 

thanks, 
karinne

---

### Post by aysiu on 2006-10-18
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows) should help.

---

### Post by karinne on 2006-10-18
I read that process; 
here below is my fdisk -l. 

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9938    79826953+   7  HPFS/NTFS
/dev/sda2            9939       30238   163059750   83  Linux
/dev/sda3           30239       30401     1309297+   5  Extended
/dev/sda5           30239       30401     1309266   82  Linux swap / Solaris
karinne@wallace-home2:~$

here's where i get stuck.
when I do sudo nano /etc/fstab,  it does not display dev/sda1 at all, so I can't edit that line. this is what it displays: 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

any ideas?  
thanks. 
karinne

---

### Post by aysiu on 2006-10-18
The bottom line--it has to be the correctly.

If it's there incorrectly, correct it.
If it's not there at all, add it.

So it would be add it: ```
/dev/sda1 /windows ntfs nls=utf8,umask=0222 0 0
```

---

### Post by catanzag on 2006-10-18
You can try to add in /etc/fstab a line like this

```

/dev/sda1 /mnt/windows ntfs user,ro 0 0

```

and then mount -a or restart, you'll have read only ntfs partition

---

### Post by anaconda on 2006-10-18
Quick and dirty solution would be to start nautilus with root rights..

gksudo nautilus

aysiu:s and catanzag:s advice is more permanent and better.

---

### Post by karinne on 2006-10-18
thank you, I will try these solutions (in the morning; i've been at a monitor [between work and home] now for about 14 hours ;/  )
have a good nite
karinne

---


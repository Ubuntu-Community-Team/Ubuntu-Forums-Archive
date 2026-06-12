---
title: "Automount Mac OS X partition?"
date: 2007-05-22
forum: Apple PPC Users
---

### Post by gamgee911 on 2007-05-22
I'm fairly sure there is, but is there a method of automounting my Mac OS X partition in Ubuntu?  I am using a dual-booting Mac OS X 10.4.9 and Ubuntu 7.04 Powerbook G4.  Thanks! :D

---

### Post by irskep on 2007-05-22
Ooh! Ooh! I know this one!

Type this in terminal:
gksudo gedit /etc/fstab

Then add this line:
/dev/hda4 	/mnt/macosx 	hfsplus user,noauto 0 0

Should work. I just had a friend tell that one to me. I haven't rebooted to try it yet though.

---

### Post by rogue6 on 2007-05-22
Or you could boot in os x and go to system preferences and and in startup disk select the mac osx disc 
and reboot from there on os x should boot on startup

---

### Post by 3rdalbum on 2007-05-23
> **rogue6 said:**
> Or you could boot in os x and go to system preferences and and in startup disk select the mac osx disc 
and reboot from there on os x should boot on startup

That's not what the OP was asking - these instructions won't automount the disk in Ubuntu.

A more comprehensive set of instructions:

Type this in terminal:
```
gksudo gedit /etc/fstab
```

Then put this into another terminal:
```
sudo fdisk -l
```

You'll see a list of partitions on your hard disk(s). The lines start with a device file name, which will look something like this: /dev/hda4. Find the line that has "HFS" in the middle column, and check that it's the correct partition by looking at the partition size column.

Then add this line to the text file, replacing "/dev/hda4" with the device file name corresponding to your partition:
```
/dev/hda4 /mnt/macosx hfsplus user,noauto 0 0
```

Save your changes and quit Gedit. In a terminal, type this:
```
sudo mkdir /mnt/macosx
```

Now reboot or execute the command "sudo mount -a", and your Mac OS X partition will mount.

---

### Post by irskep on 2007-05-23
I'm sorry, I forgot to mention the bit about replacing the HD identifier. Thanks for fixing that for me.

---

### Post by gamgee911 on 2007-05-23
Oh wow, **Thanks a lot!** :)  That was really helpful.  Thanks again!

---

### Post by SycloneMedia on 2007-05-24
Actually, since you want to _automount_, the previous posts have been using "noauto" in the line which is incorrect... should obviously be "auto" to automount the partition.

Additionally, this is important, make sure the partition you want to access has journaling turned OFF... because there have been reports of Linux not being friendly with HFS+ w/ Journaling turned on. You don't want to destroy any data or cause problems on either end.

---

### Post by gamgee911 on 2007-05-24
I've noticed that it mounts as read only, is there a way to make it writeable?  Thanks

---

### Post by SycloneMedia on 2007-05-25
> **gamgee911 said:**
> I've noticed that it mounts as read only, is there a way to make it writeable?  Thanks

add a 'rw' to the options like:

```
rw,user,auto
```

However there are a few quirks with using HFS+ in Linux as I've found doing the same. Mainly, you have to be mindful of freezes and/or crashes in your OS X system and maybe Ubuntu while it is mounted. I don't exactly know why, but after such a crash, Ubuntu won't be able to write to the disk again (permissions will be denied even though everything is correctly set) until you boot back into OSX and go and do some successful meaningless access or write to that partition (like create a blank folder, and then delete if you wish). And then when you boot up Ubuntu again it should let you write to it again.

---

### Post by WaySensei on 2007-12-25
I have tried this on my Intel Macbook Pro Core Duo, but receive the following errors: 
[mntent]: line 8 in /etc/fstab is bad
[mntent]: line 10 in /etc/fstab is bad

My /etc/fstab looks like this:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=df5f33bf-8cc8-49c3-946d-24ef8a65dd9d /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=3F3C-1AF6  /media/EFI      System  Partition       vfat    defaults,utf8,umask=007,gid=46 0 1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/sda2	/mnt/macosx	hfsplus user, auto	0	0

What am I doing wrong?

---


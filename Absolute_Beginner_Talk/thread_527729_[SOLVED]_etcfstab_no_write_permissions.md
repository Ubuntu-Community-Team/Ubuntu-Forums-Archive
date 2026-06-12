---
title: "[SOLVED] /etc/fstab no write permissions"
date: 2007-08-16
forum: Absolute Beginner Talk
---

### Post by johntkucz on 2007-08-16
whoops. was trying to rename the mount point of my internal hd and an external flash drive, now I don't have permissions to write the external flash.  

I'm trying to get read-write access to /dev/sdc1 (mounted at e2)
here's etc/fstab

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=3a79ad82-eb61-4d85-a3b3-08b8e5396b4a /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=eeb84bb0-7e4e-463a-8ad3-916bf67774c1 /home           ext3    defaults        0       2
# /dev/hda1
UUID=9858328CE07FB76E /media/i80 ntfs    defaults,nls=utf8,umask=007,gid=46        0       1
#  /dev/sda3  swap
UUID=087fa5ff-dd64-478e-9343-257b9765c2f8 none            swap    sw              0       0
# cdroms
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto     0       0
# /dev/sdc1 --VFAT External Travel Drive 2bb
UUID=441D-0DF8 /media/e2 vfat  rw,nodev,shortname=mixed,utf8,umask=077 0 1
#UUID=441D-0DF8 /media/e2 vfat  rw,nosuid,nodev,shortname=mixed,utf8,umask=077 0 1
```

any ideas? thanks.

---

### Post by Bachstelze on 2007-08-16
```
UUID=441D-0DF8 /media/e2 vfat  rw,nodev,shortname=mixed,utf8,umask=077,uid=1000 0 1
```

This should work better :)

---

### Post by st33med on 2007-08-16
> **HymnToLife said:**
> ```
UUID=441D-0DF8 /media/e2 vfat  rw,nodev,shortname=mixed,utf8,umask=077,uid=1000 0 1
```

This should work better :)

What if he wants other users to access it?

---

### Post by johntkucz on 2007-08-16
wow, love the instant response around here! Jeez.  

in order to test the new fstab, I can't umount "file system busy" for some reason but I have no programs open.

nosuid makes sense like it would help, though.  thanks

---

### Post by johntkucz on 2007-08-16
how do you close a synaptic that might be running in the background? maybe that's why the file system is busy.

---

### Post by st33med on 2007-08-16
Check the system processes.

System>>Preferences>>System ...

Dang! Forgot that last bit!

---

### Post by Bachstelze on 2007-08-16
> **st33med said:**
> What if he wants other users to access it?

Then he tells us so and we tell him how do do it.

---

### Post by johntkucz on 2007-08-17
> **HymnToLife said:**
> Then he tells us so and we tell him how do do it.

Yeah. thanks hym, "what if..."s could go on for ever.   one step at a time.

okay, 

now when I sudo mount /dev/sdc1   the image doesn't even load in places or sidepane. but the shell commands mount  /dev/sdc1 and umount /dev/sdc1 process.

---

### Post by kerry_s on 2007-08-17
> **johntkucz said:**
> Yeah. thanks hym, "what if..."s could go on for ever.   one step at a time.

okay, 

now when I sudo mount /dev/sdc1   the image doesn't even load in places or sidepane. but the shell commands mount  /dev/sdc1 and umount /dev/sdc1 process.

sudo mount /dev/sdc1 /media/e2

---

### Post by johntkucz on 2007-08-17
okay, when I umount /dev/sdc1 and comment out it's reference in fstab, then unplug and replug it in manuall, it loads with read-write permissions

```
/dev/sdc1 /media/disk vfat rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077 0 0
```

shows up in mtab when I plug it in manuall and it uses it's preprogrammed mountpoint /media/disk.


How do I change the mount point so it auto-loads to /media/e2?  

When I tweak fstab, I can get it to load as e2, but then the file permissiosn are locked down.

btw, different between mtab and fstab?  mtab gets written to actively.

---

### Post by johntkucz on 2007-08-17
> **kerry_s said:**
> sudo mount /dev/sdc1 /media/e2

Is that format
sudo mount /dev/devicename /media/mountpoint

I haven't included the /media/mountpoint part before, but it still mounted, how is that?

---

### Post by johntkucz on 2007-08-17
when I umount the drive, it still shows up in the side pane as "Memorex TD Classic 003B" .  From where does it get that name?  The actual drive itself?

---

### Post by johntkucz on 2007-08-17
okay very interesting 

sudo mount /dev/sdc1 /media/e2

mounts, but results in read-only.

---

### Post by johntkucz on 2007-08-17
I tried

```
sudo chmod a+w medial/e2
```

That works, but then when I 

```
sudo mount /dev/sdc1 /media/e2
```

the file permissions of e2 revert back.

---

### Post by johntkucz on 2007-08-17
> **st33med said:**
> Check the system processes.

System>>Preferences>>System ...

Dang! Forgot that last bit!

i don't have a panel that begins "system" under system>preferences

---

### Post by st33med on 2007-08-17
Oh, now I remember! System moniter.

Of course, you might be running Kubuntu and it is Kmoniter (or something like that).

---

### Post by johntkucz on 2007-08-17
okay, do you add read-write permissions to fstab,  I guess that'll solve it (rw is mtab).

---

### Post by johntkucz on 2007-08-17
> **johntkucz said:**
> okay, when I umount /dev/sdc1 and comment out it's reference in fstab, then unplug and replug it in manuall, it loads with read-write permissions

```
/dev/sdc1 /media/disk vfat rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077 0 0
```

shows up in mtab when I plug it in manuall and it uses it's preprogrammed mountpoint /media/disk.


How do I change the mount point so it auto-loads to /media/e2?  

When I tweak fstab, I can get it to load as e2, but then the file permissiosn are locked down.

btw, different between mtab and fstab?  mtab gets written to actively.

okay figured this out.  mount and umount writes directly, actively to the mtab file.  Fstab, on the other hand, gets accessed during boot sequence and other than that does not get written to actively, but commands can access it (mount).

---

### Post by johntkucz on 2007-08-17
> **st33med said:**
> Oh, now I remember! System moniter.

Of course, you might be running Kubuntu and it is Kmoniter (or something like that).

that's system>administration

and yes, I love system monitor.  My newly discovered best friend!  But how will that help me here? I already know my device name.  Oh RIGHT the background processes!  I just rebooted, but will remember that in the future.

---

### Post by johntkucz on 2007-08-17
so still don't know how to have it boot to e2 with full permissions.

---

### Post by johntkucz on 2007-08-17
redirected

[http://ubuntuforums.org/showthread.php?p=3203984#post3203984]("http://ubuntuforums.org/showthread.php?p=3203984#post3203984")

---


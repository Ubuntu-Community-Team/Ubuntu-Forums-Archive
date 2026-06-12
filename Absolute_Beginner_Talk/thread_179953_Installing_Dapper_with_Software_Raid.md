---
title: "Installing Dapper with Software Raid"
date: 2006-05-21
forum: Absolute Beginner Talk
---

### Post by oboontoo on 2006-05-21
So how is one supposed to install Dapper with software raid. Is it even possible?

I have 4 hds on 74 Gb that I want to install Dapper on but I can't get it to work

This is how I laid it out using the text installer
```
/boot  100 Mb raid 1 (100 mb sda, 100mb sdb)
swap      4 Gb raid 0 (2 Gb sda, 2 Gb sdb)
/home     9 Gb raid 5 (3 GB sda, 3 Gb sdb, 3 Gb sdc, 3 Gb sdd)
/tmp       4 Gb raid 0 (2 Gb  sdc, 2 Gb sdd)
/        200 Gb raid 5 (69 Gb sda, 69 Gb sdb, 69 Gb sdc, 69 Gb sdd)
```

Disk layout
sda
```
    /boot 100 mb (raid 1)
    swap   2 Gb   (raid 0)
    /home  3 Gb   (raid 5)
    /        69 Gb  (raid 5)
```
sdb
```
    /boot 100 mb (raid 1)
    swap   2 Gb   (raid 0)
    /home  3 Gb   (raid 5)
    /        69 Gb  (raid 5)
```
sdc
```
   /tmp    2  (Gb raid 0)
   /home  3  (Gb raid 5)
   /        69 (Gb raid 5)
```
sdd
```
   /tmp    2  Gb (raid 0)
   /home  3  Gb (raid 5)
   /        69 Gb (raid 5)
```

I finish the installer, which runs to completion without any issues. Rebooted
and it stops at
mount sys /root/sys no such file or directory (or something like that)
and all I get is a bash shell.

I think I read that the text install is broken and one should use the live CD. So I tried the live CD, but I don't seem to get an option to use software raid in the partitioning tool. 

How do I achieve what I want? Am I trying to do something stupid?

Martin

---

### Post by therunnyman on 2006-05-21
You know, I had almost exactly the same problem.  It's been acknowledged as a problem over at launchpad (the bug-report place), and they're evidently working on it; it's something to do with udev not working as closely as it should with the installer and GRUB.  My suggestion is wait until the final release (I know, I can't wait either).

If you feel like it, you can edit GRUB by pressing "E" on whatever kernel you want.  There, you'll be able to edit which device Dapper believes is the root device.  Direct it to "root=/dev/sdb1" or whatever works (in my case, Dapper believed itself to reside on sdb1, rather than sda1, where it actually was).  That way, you'll at least be able to boot into Dapper, and mess with it until something happens.

Tell me something: did Breezy pick up your RAID?  It picked mine up just fine, not a hitch.

therunnyman

---

### Post by nickle on 2006-05-21
I have no problems with a RAID 1 installation with 2 HDs; it worked on Breezy and now works on Dapper... Not much help I am afraid, but I guess it is not a general problem for RAID 1 at least.

---

### Post by oboontoo on 2006-05-21
[QUOTE=therunnyman]
If you feel like it, you can edit GRUB by pressing "E" on whatever kernel you want.  There, you'll be able to edit which device Dapper believes is the root device.  Direct it to "root=/dev/sdb1" or whatever works (in my case, Dapper believed itself to reside on sdb1, rather than sda1, where it actually was).  That way, you'll at least be able to boot into Dapper, and mess with it until something happens.

Tell me something: did Breezy pick up your RAID?  It picked mine up just fine, not a hitch.
therunnyman[/QUOTE]

Just my luck that I had to stumble upon a bug on my first attempt with Linux.
Thanks for the tip. I've now managed to get my Dapper up off the ground.
For some reason grub had "root=/dev/md4" which is the /tmp partition. When I fixed that it could at least mount root, but then it bailed out saying there were bad disks so I had a look in fstab and ofcourse it was all messed up in there as well.
/dev/md4 / which should have been /dev/md3
/dev/md3 /home which should have been /dev/md2
/dev/md2 /tmp which should have been /dev/md4

After fixing that it booted okay.

As for detecting raid (I assume you meant Dapper as I've never installed Breezy on this machine) it seems very flaky and software raid doesn't seem to be supported if you install via the LiveCD, which is supposed to be the recommended way.
When I get into the partitioning tool , after having already set up my partitions and raid configuration in a previous run, it doesn't detect the raid so I choose configure software raid and do a create MD device, but then it screems something along the lines of "none available, please delete an MD device first" if I then go back it will list all the previously created raid arrays.

/Martin

---


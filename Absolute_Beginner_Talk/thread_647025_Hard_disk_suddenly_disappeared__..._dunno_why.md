---
title: "Hard disk suddenly disappeared  ... dunno why?"
date: 2007-12-21
forum: Absolute Beginner Talk
---

### Post by CptnFantasy on 2007-12-21
I have a 320 gig NTFS volume which ubuntu is no longer aware of...and all I did was reboot. windows sees the drive and I can find its folder under /media/hdb1in ubuntu, but its empty. any suggestions?

---

### Post by logos34 on 2007-12-21
post fstab file:

**cat /etc/fstab**

and 

**mount**

You running feisty or gutsy or what?  Have ntfs-3g installed?

---

### Post by taurus on 2007-12-21
Sounds like you didn't shut down windows cleanly.  So, you have two options:

1.  Boot into windows and shut it down cleanly.  Don't use hibernate or other mode.

or

2.  Use the force option to mount it.

```

sudo mount -t ntfs /dev/hdb1 /media/hdb1 -o force
df -h
```

---

### Post by CptnFantasy on 2007-12-21
I shut down windows cleanly, no help, so I tried the force mount and was given the following message: 
$MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/hdb1': Input/output error
NTFS is either inconsistent, or you have hardware faults, or you have a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows TWICE. The usage of the /f parameter is very
important! If you have SoftRAID/FakeRAID then first you must activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for the details.
I assume that the chkdisk /f command is for the windows prompt...so im am going to investigate that in just a moment. 
by the way, I have gutsy gibbon 64bit

---

### Post by CptnFantasy on 2007-12-21
nope did not work...
here is the fst file:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda6
UUID=686f0f39-d8ee-4d4d-8ec7-55bd917c3f3a /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=FC306AD1306A9306 /media/hda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/hda5
UUID=9E90923F90921DB9 /media/hda5     ntfs    defaults,umask=007,gid=46 0       1
# /dev/hdb1
UUID=067CE63E7CE627DF /media/hdb1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/hda7
UUID=045662b0-3fba-4150-8b22-eaf343365b41 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
but i just looked in a command line reference file at the microsoft website and saw that i had used the chkdsk  command improperly...no wonder it didn't work...gonna try it the right way now...

---


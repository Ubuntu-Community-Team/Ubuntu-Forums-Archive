---
title: "Repairing the Filesystem"
date: 2007-09-06
forum: Apple PPC Users
---

### Post by ajamoffatt on 2007-09-06
I am running on an ibook G4 1.2GHz.  I started osx from my external firewire hard drive to reset some permissions for access from Ubuntu, and then cloned that osx disk onto a free partition of my ibook drive.  When starting back up from the internal drive, yaboot came up just fine and started Ubuntu (The macosx partition nor the External FW drive were not listed, though, as options. Is there a way to fix this?).  During startup, though, the fsck file system check failed on the linux Ext3 partition.  It cannot fix it becuase this is the Ubuntu drive.
Here is the fsck log:

```
Log of fsck -C -R -A -a 
Wed Sep  5 21:19:50 2007

fsck 1.40-WIP (14-Nov-2006)
fsck.ext3: Unable to resolve 'UUID=3d784982-9e69-4b4b-85ff-8fcdbfb97f3d'

fsck died with exit status 8
```



 Ubuntu still seems to work fine if I just ignore the errors and press CTR-D, but it would be nice to fix this, and I am very new to Linux.  Thanks.  Oh, and running fsck on the partition from the Desktop CD returned no errors.

---

### Post by frog_pilot on 2007-09-06
The manpege for [e2fsck]("http://linux.die.net/man/8/e2fsck") says > Exit Code
The exit code returned by e2fsck is the sum of the following conditions:
0 - No errors
1 - File system errors corrected
2 - File system errors corrected, system should
be rebooted
4 - File system errors left uncorrected
8 - Operational error
16 - Usage or syntax error
32 - E2fsck canceled by user request
128 - Shared library error

maybe that for some reason the uuid has changed or you made a mistake writing th uuide in the fstab

```
sudo fdisk -l
``` gives you a list of your harddisks and their partitions.
```
sudo vol_id -u /dev/hdXX or sdXX
``` for the partition where the root-filesystem is on shows you the correct UUID

---

### Post by ppietryga on 2007-09-06
> **ajamoffatt said:**
> 
(The macosx partition nor the External FW drive were not listed, though, as options. Is there a way to fix this?).

Have no experience with FireWire, but maybe you need some modules loaded to support FireWire drives (something like usb_storage fo USB drives).
And as for MacOSX partition (I also haven't any experience with mac) list the partition table:
```

sudo fdisk -l

```
write down what's in the 'Device' column for your Mac Partiotion (i guess it shoud be something that has HFS or something in 'System' column). Then edit the /etc/fstab  file and add something like this:
```

/dev/sda1         /media/MacOSX       hfs      defaults     0       0

```
The /dev/sda1 is whot you  find in Device column. The /media/MacOSX directory has to exist (you may use whatever you want here).
After that you may run:
```

suod mount /media/MacOSX

```
If it fails try loading a hfsplus module (which I belive is the preferred file system for Mac OSX).
```

sudo modprobe hfsplus

```

> **ajamoffatt said:**
> 
```
Log of fsck -C -R -A -a 
Wed Sep  5 21:19:50 2007
fsck 1.40-WIP (14-Nov-2006)
fsck.ext3: Unable to resolve 'UUID=3d784982-9e69-4b4b-85ff-8fcdbfb97f3d'
fsck died with exit status 8
```

Looks like the UUID of your partition has changed. If you know what is the partition, than  you can edit the /etc/fstab file and change the line containig this UUID with the /dev/sdax (whatever you have on your system).

---

### Post by ajamoffatt on 2007-09-08
Thanks for the response.  I found that I had the newly reformated osx partition still listed as an ext3 file system by fstab.  fsck.ext3 didn't quite understand how to scan that.  So that's solved, but I still can't get that osx partition to show up in the yaboot menu.  I added it to both fstab and mtab as an hfsplus, and to yaboot.conf as
```
 macosx=/dev/hda5
```
 but it still doesn't show up.  I have a feeling I'm missing something simple.  I'm just so scattered trying to get different things to all work.  Could someone please clarify the usage of fstab and mtab? Thanks.  I appreciate the help.

Aaron M

---

### Post by pxwpxw on 2007-09-08
> **ajamoffatt said:**
> Thanks for the response.  I found that I had the newly reformated osx partition still listed as an ext3 file system by fstab.  fsck.ext3 didn't quite understand how to scan that.  So that's solved, but I still can't get that osx partition to show up in the yaboot menu.  I added it to both fstab and mtab as an hfsplus, and to yaboot.conf as
```
 macosx=/dev/hda5
```
 but it still doesn't show up.  I have a feeling I'm missing something simple.  I'm just so scattered trying to get different things to all work.  Could someone please clarify the usage of fstab and mtab? Thanks.  I appreciate the help.

Aaron M

I am only commenting about the yaboot.conf macosx setting here.
I assume you can boot macosx using the Option key.

The  macosx=/dev/hda5 option in yaboot.conf is for the first stage ofboot menu ( the  l c x one ). But yaboot,  which is loaded after ofboot.b , cannot boot macosx. You need to rerun the yaboot bootstrap installer, ybin, from ubuntu to make that change effective, then the x option will be on the first stage (ofboot) menu. (man yaboot.conf explains it )

 For example if your Apple_Bootstrap NewWorld boot partition is hda2 (change it for your number)
```

 sudo ybin -b /dev/hda2 -v

```
 Run it with the -v (verbose ) to see what it is doing.

Read man ybin, you can specify the boot partition or let it find it.

But note that I am assuming you have everything back on the internal drive,  and ubuntu is running well.

If you have any worries about that, post your complete /etc/yaboot.conf and a listing of your drive partitions
```

sudo mac-fdisk -l

```

---


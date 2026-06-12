---
title: "USB Thumb Drive quit working under 7.10"
date: 2008-02-04
forum: Absolute Beginner Talk
---

### Post by Glenn Picklesimer on 2008-02-04
After upgrading to 7.10 my USB thumb drive quit working.  Still works in MS Windows and Kubuntu.  When I insert it in the USB port I get a dialog box that says "Cannot mount volume" and the details say:

mount:wrong fs type, bad option, bad superblock on /
dev/sdb1,    missing codepage or helper program,
or other error         In some cases useful info is found
in syslog - try         dmesg | tail or so

Nothing else changed except the upgrade.  I can't figure out how to get it to mount (I'm a little new at this).  Can anyone help?  Thanks in advance!

---

### Post by Blutack on 2008-02-04
Could you post the output of
> dmesg | tail
please?

---

### Post by Glenn Picklesimer on 2008-02-04
Ok, here it is:

[ 2706.504000] sdb: Mode Sense: 43 00 00 00
[ 2706.504000] sdb: assuming drive cache: write through
[ 2706.508000] SCSI device sdb: 502880 512-byte hdwr sectors (257 MB)
[ 2706.508000] sdb: Write Protect is off
[ 2706.508000] sdb: Mode Sense: 43 00 00 00
[ 2706.508000] sdb: assuming drive cache: write through
[ 2706.508000]  sdb: sdb1
[ 2706.548000] sd 2:0:0:0: Attached scsi removable disk sdb
[ 2706.548000] sd 2:0:0:0: Attached scsi generic sg2 type 0
[ 2707.052000] FAT: Unrecognized mount option "usefree" or missing value

Thanks!

---

### Post by Blutack on 2008-02-04
Hmm, could you go into "Computer", find your drive and go into the properties.  Then see if the mount options include usefree and if they do, remove it.

---

### Post by Glenn Picklesimer on 2008-02-04
usefree is not in there

---

### Post by Blutack on 2008-02-04
It's a known bug, sorry!
Fix is here:
[https://bugs.launchpad.net/ubuntu/+source/gnome-mount/+bug/151025](https://bugs.launchpad.net/ubuntu/+source/gnome-mount/+bug/151025)
Specifically
> Hit alt-f2, type in conf-editor and navigate to /system/storage/default_options/vfat/mount_options, and then remove the "usefree" option from the list. Exit gconf-editor, and try hotplugging your drive again. It works :-)

---

### Post by Glenn Picklesimer on 2008-02-04
That works!  Thank you very much for your time.

Now for the newbie question--is that file equivalent to the windows registry?

---

### Post by Blutack on 2008-02-04
You are welcome!

Erm...yes and no.
Gconf-editor is just a pretty front-end for a set of files.
They are in plain text and located in a hidden .gconf folder in your home folder.
You can see it by pressing Control-H.
So, yes in the sense it provides a central mechanism for controlling the settings of some programs, mostly Gnome ones.  No in the sense that it can be used to hide nasties.  It also doesn't fill up and slow down.

---

### Post by Glenn Picklesimer on 2008-02-04
Ok, that makes sense.  I see I have a lot of learning to do.  But this fix keeps me working.  Thanks again.

---

### Post by Blutack on 2008-02-04
No problem, should be fixed in Hardy.

---


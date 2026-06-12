---
title: "having a bad day - a real bad day!!!"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by tchoklat on 2007-06-15
All is not going to plan toady;
1.  lost my HDD partitions
2.  Unable to find the lost data
3.  Difficulty in loading a new OS.

Help me please with problem four!

OS new install on freshly formatted HDD

When I put a DVD/CD in the burner I am returned this great sounding message:

mount: block device /dev/hda is write-protected, mounting read-only mount: wrong fs type, bad option, bad superblock on /dev/hda, missing codepage or other error In some cases useful info is found in syslog - try dmesg | tail or so

Part of my fstab is here - not sure about the burner entry!

# fd: H1440
/dev/fd0        /mnt/floppy     auto    user,exec,rw,noauto     0 0

# cdrom: PIONEER DVD-RW DVR-112D
#       /dev/hda        /mnt/cdrom      auto    user,exec,ro,noauto     0 0

# /dev/hdb1, size=20627397, type=131: Journalised FS: ext3 (primary)
/dev/hdb1       /mnt/hdb1       ext3    user,exec,rw,noauto     0 0

# /dev/hdb10, size=16370172, type=131: Journalised FS: ext3 (extended)
/dev/hdb10      /mnt/hdb10      ext3    user,exec,rw,noauto     0 0

# /dev/hdb11, size=30153942, type=131: Journalised FS: ext3 (extended)
/dev/hdb11      /mnt/hdb11      ext3    user,exec,rw,noauto     0 0

# /dev/hdb5, size=4144707, type=130: Linux swap (extended)
/dev/hdb5 swap swap defaults 0 0

# /dev/hdb6, size=25254117, type=131: Journalised FS: ext3 (extended)
/dev/hdb6       /mnt/hdb6       ext3    user,exec,rw,noauto     0 0

# /dev/hdb7, size=28049427, type=131: Journalised FS: ext3 (extended)
/dev/hdb7       /mnt/hdb7       ext3    user,exec,rw,noauto     0 0

# /dev/hdb8, size=27535347, type=131: Journalised FS: ext3 (extended)
/dev/hdb8       /mnt/hdb8       ext3    user,exec,rw,noauto     0 0

# /dev/hdb9, size=4160772, type=130: Linux swap (extended)
/dev/hdb9 swap swap defaults 0 0

Help me I am losing it!

---

### Post by Garyu on 2007-06-15
I'm not sure about your problem. Are you saying you want to burn a downloaded .iso to install a fresh OS but the burning software won't work your drive? Or are you saying you get that error when you try to launch the installer on boot? Please be more descriptive of your problem.

As for your lost data...
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
Take a look at this app. Available for both linux and windows. It will recover data from any disk even without partition information. It can recover other files than photos as well. There might be other tools that can recover other things too, but this is the one I've been using lately and it has been working very well for me.

---

### Post by tchoklat on 2007-06-15
Thanks for your response.

My issue is that I cannot mount the DVD burner. It is just the most recent of my issues today!!!

When I click on the icon for the DVD/CD it says it is unmounted and when I click on 'mount' I get that error!

Tony

---

### Post by Garyu on 2007-06-15
Well, in your fstab it seems as the cdrom mounting is commented out... for some reason...

This is my cdrom line from my fstab:
```
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto 0 0
```
But this is not a burner...

---

### Post by tchoklat on 2007-06-15
Thanks garyu, 

This is the fstab that gets the DVD burner to read DVDs but is will not recognise CDs!

/dev/hda /media/dvdrw udf,iso9660 user,noauto 0 0

Anyone???

---


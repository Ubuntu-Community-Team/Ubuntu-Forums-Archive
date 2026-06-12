---
title: "No permission to read or delete files on USB drive"
date: 2007-02-20
forum: Absolute Beginner Talk
---

### Post by oceanspray on 2007-02-20
I have 3 hard drives, two internal SATA ones and an external USB drive (/dev/sdc5).  Have lots of music on the USB drive and Ubuntu is able to play, or view all of it, only I have NO permission to edit any file, only to access it.  Tried changing permissions but I can't.  Get this error every time:

The permissions could not be changed.

Couldn't change the permissions of "Music" because it is on a read-only disk

The filesystem is NTFS.

Would dearly like to edit what's on the disk, can anyone help?

Thanks oodles!

---

### Post by charles.g.moore on 2007-02-20
I tink that NTFS volumes are automatically mounted read only, you have to use another thing to allow mounting with read/write capabilities

[http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009)

---

### Post by bodhi.zazen on 2007-02-20
Try ntfs-config :

[http://doc.gwos.org/index.php/Ntfs-config](http://doc.gwos.org/index.php/Ntfs-config)

ntfs-config is a gui front end for ntfs-3g ;)

---

### Post by charles.g.moore on 2007-02-20
> **bodhi.zazen said:**
> Try ntfs-config :

[http://doc.gwos.org/index.php/Ntfs-config](http://doc.gwos.org/index.php/Ntfs-config)

ntfs-config is a gui front end for ntfs-3g ;)

Nice, I guess i'll have to check that out too...
You learn something new every day

Thanks
Chuck

---

### Post by oceanspray on 2007-02-20
Wow, that's a full plate, will read up on it and report back!

---

### Post by Fully216 on 2007-02-20
By default, any NTFS partition will be read only.  Linux as of now does not fully support NTFS.  Do nor fret just yet; there are work arounds however.  They are still considered 'beta' so be warned.

A great site that will give you more information and detail than I ever could is [www.linux-ntfs.org](www.linux-ntfs.org).  They are the ones that develop ntfs-3g, which is a package you might consider using to write to your NTFS partition.  On a side note, it is currently only available for 32 bit machines, so sorry 64 bit users (me included).

Captive ntfs is a great program that lets you read and write to NTFS.  You can find a post about it here:

[http://ubuntuforums.org/showthread.php?t=10175](http://ubuntuforums.org/showthread.php?t=10175)

Hope this helps!

---

### Post by oceanspray on 2007-02-20
> **charles.g.moore said:**
> I tink that NTFS volumes are automatically mounted read only, you have to use another thing to allow mounting with read/write capabilities

[http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009)

Had a bad feeling about this (found the explanation to be very confusing, VERY!!) but went ahead anyway and after rebooting Ubuntu doesn't recognize the drive anylonger, gives me this error:

Unable to mount the selected volume.

[mntent]: line 11 in /etc/fstab is bad

mount: can't find /dev/sdc5 in /etc/fstab or /etc/mtab

:confused:

---

### Post by oceanspray on 2007-02-20
Fully216, sorry it isn't available yet for your 64 bit machine, it is for my 32 bit one.  Am installing Captive now, see if it does any good.

Thanks!

---

### Post by givré on 2007-02-20
> **Fully216 said:**
> 

Captive ntfs is a great program that lets you read and write to NTFS.  You can find a post about it here:

[http://ubuntuforums.org/showthread.php?t=10175](http://ubuntuforums.org/showthread.php?t=10175)

You should not advice captive-ntfs, this is a terribly dangerous tool, which is no more maintain now.

---

### Post by oceanspray on 2007-02-22
Just wanted to add that i chickened out on using any of the software folks recommended my using; couldn't afford to lose my music collection and so running out of options, reinstalled Ubuntu.

Will edit those files from within XP and wait patiently for new software that "safely" lets me change stuff so as to enable my editing files on the USB drive.

Thanks for helping!

---

### Post by lanchongzi on 2007-02-23
I have a similar problem
I am using a PSP (Playstation Portable ) and I cant acces it
is there a 'non-risky' way?
otherwise I will just use my XP partition for this

---


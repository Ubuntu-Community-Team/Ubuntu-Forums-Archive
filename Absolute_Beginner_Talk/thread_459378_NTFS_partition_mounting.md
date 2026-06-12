---
title: "NTFS partition mounting?"
date: 2007-05-30
forum: Absolute Beginner Talk
---

### Post by Neon_Knight on 2007-05-30
okay, I had a little problem installing/uninstalling KDE earlier, and now, I can't mount my NTFS partition anymore.

Before I was able to read and write my NTFS (with the third party thing), but now whenever I click on "Hda2" in "computer" I get the following message:

```

You do not have the permissions necessary to view the contents of "hda2".

```

and I'm not sure how to solve this.

I need to access my NTFS partition because that holds all of my important files that I frequently access.

I try doing
```

gksudo nautilus

```
but I get the following:
```

(nautilus:7550): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

```

but

```

sudo nautilus

```

seems to work, however if I close the window that comes up, I lose all ability to read the partition, when I'm looking for a permanent solution to this.

Any suggestions?



And another thing, when I click the red button in the top right to shut down or restart, both the 'shut down' AND the 'restart' buttons are gone. There's only 'Hibernate','Switch User','log off' and 'Lock Screen'.




Oh yes, I'm using Ubuntu Dapper Drake 6.06

---

### Post by Inxsible on 2007-05-30
Do not worry about the gksudo nautilus error. Its a harmless bug thats already been reported.
 
Try this to mount your drive
```
sudo mount -t ntfs-3g /dev/sdX /media/sdX -o iocharset=utf8,umask=000
```
 
Replace X with your drive letter and number

---

### Post by oilchangeguy on 2007-05-30
also try this:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by Neon_Knight on 2007-05-30
Okay, I tried Inxsible's suggestion, this is what happened:


```

david@david-desktop:~$ sudo mount -t ntfs-3g /dev/hda2 /media/hda2 -o iocharset=utf8,umask=000
WARNING: Deficient Linux kernel detected. Some driver features are
         not available (swap file on NTFS, boot from NTFS by LILO), and
         unmount is not safe unless it's made sure the ntfs-3g process
         naturally terminates after calling 'umount'. If you wish this
         message to disappear then you should upgrade to at least kernel
         version 2.6.20, or request help from your distribution to fix
         the kernel problem. The below documentation has more information:
         /usr/share/doc/ntfs-3g/README.Debian

```

Help?

---

### Post by aysiu on 2007-05-30
There's no *ntfs-config* for Ubuntu 6.06, so you'll have to do [something a little more complicated](http://ubuntuforums.org/showthread.php?t=217009).

---

### Post by Neon_Knight on 2007-05-30
Ah, I see.

Thank you very much, aysiu,  that fixed it!

Tr00 points for you.


**EDIT:**

Although...

It's not quite as it was before.

Before, I had a hda2 link on the desktop, and whenever I opened the File Browser, it used to have hda2 on the panel on the left.  It's not a huge problem, but it'd be nice to have it complete as it was before. ^^

---

### Post by aysiu on 2007-05-30
I don't know about it being in the file browser, but you should be able to easily create a link to it on the desktop. Just middle-click-drag the folder (say, /media/hda2, or whatever it's called) to the desktop and select *link here* when you let go of the scroll wheel.

---


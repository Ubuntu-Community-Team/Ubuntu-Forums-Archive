---
title: "Connect to OSX share from Ubuntu 8.10"
date: 2009-04-08
forum: Apple Hardware Users
---

### Post by wardjame on 2009-04-08
I have a mac mini with an external hard drive attached via usb and shared over my network.  The drive is accessible to windows machines on my network but is invisible to Ubuntu.

Mac is running OSX 10.5.6 on an Intel.

In case it makes any difference the drive is formatted Mac OS Extended (Journaled).

Any thoughts on how I can get connected to it would be much appreciated.

---

### Post by Joeb454 on 2009-04-08
Thread moved to Apple Users :)

Are you sharing via afp or smb? I believe you'll need to be using samba to get ubuntu to see it.

Or sftp I guess :p

---

### Post by cyberdork33 on 2009-04-08
[http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534)

---

### Post by wardjame on 2009-04-17
Thanks joeb454.  I had it set to use afp instead of smb.  works like a charm now.

---


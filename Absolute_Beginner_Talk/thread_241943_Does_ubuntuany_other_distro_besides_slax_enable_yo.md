---
title: "Does ubuntu/any other distro besides slax enable you to access your windows NTFS?"
date: 2006-08-23
forum: Absolute Beginner Talk
---

### Post by systemintheglitch on 2006-08-23
Sorry, just wondering.. 

Any other distros allow this easily out of the box?

---

### Post by jlachovsky on 2006-08-23
I have heard the DVD version of Knoppix has full read-write to NTFS "out of the box", but not confirmed.  As far as Ubuntu goes you can always install NTFS-3g which enables NTFS read-write, but their isn't 64 bit support as of yet.

---

### Post by bodhi.zazen on 2006-08-23
They all do. There are instructions on the Ubuntu start guide for example:

[http://ubuntuguide.org/wiki/Dapper#Windows](http://ubuntuguide.org/wiki/Dapper#Windows)

Or this may be more up to date:

[http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009)


I can access (rw) ntfs with Debian, Ubuntu, ELive, Zenwalk, and Arch to name a few.

What kind of problem are you having?

---

### Post by crispy_420 on 2006-08-23
I hear any attempt to write to NTFS is risky and could cause a loss of data. Why do you need this support? External drive? Or shared drive. If shared you should look into ext3 support for windows.

---


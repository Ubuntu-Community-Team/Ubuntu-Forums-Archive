---
title: "Configuring X"
date: 2005-09-21
forum: Absolute Beginner Talk
---

### Post by Martin on 2005-09-21
Hi, I recently filled the disk on my laptop up completely. This caused X.org to fail. Once I finally managed to log back in and delete some files X still won't start. Does anybody have any ideas what I need to do? I've been looking for something on the system along the lines of Xconfig or something to re-configure but I can't seem to find anything. The error I get is that ..core devices could not be loaded.. 

Martin

---

### Post by SilentCacophony on 2005-09-21
the general way to reconfigure X is with:

sudo dpkg-reconfigure xserver-xorg

Hopefully there was no data loss.

---


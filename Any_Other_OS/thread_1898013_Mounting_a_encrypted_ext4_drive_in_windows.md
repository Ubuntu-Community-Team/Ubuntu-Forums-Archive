---
title: "Mounting a encrypted ext4 drive in windows?"
date: 2011-12-20
forum: Any Other OS
---

### Post by MasterNetra on 2011-12-20
I was wondering if anyone knew how to mount a encrypted ext4 partition (Drive) in windows? Tried using Ext2Fsd, 0.51 is suppose to be able to see and mount ext4 but I guess not encrypted ext4 sense it sees it as "raw". Been trying to find a way using something that will do it for windows 7, even though I am trying out Windows 8 (DP). I would rather not have to use a live-cd everytime I want something from my USB drive.

---

### Post by MasterNetra on 2011-12-20
Just tried ext2read, no dice with it either. :/

---

### Post by oldos2er on 2011-12-20
Moved to Other OS/Distro Talk.

---

### Post by MasterNetra on 2011-12-20
Great to obscurity the thread goes...

---

### Post by mips on 2011-12-20
I don't think you are going to come right with this in all honesty....

---

### Post by MasterNetra on 2011-12-20
> **mips said:**
> I don't think you are going to come right with this in all honesty....

? I don't understand what your trying to say.

---

### Post by HermanAB on 2011-12-20
Hmm, install virtualbox on Windows.  Install Linux in virtualbox.  install the guest additions and share the encrypted folder with Windows.

---

### Post by mips on 2011-12-21
> **MasterNetra said:**
> ? I don't understand what your trying to say.

1. Windows has limited 3rd party support for Ext4
2. Based on 1 above encryption on Ext4 could be a potential no go.

Either way have a look at Ext2Fsd & FreeOTFE, maybe one of them will work for you.

[http://en.wikipedia.org/wiki/Dm-crypt#Compatibility](http://en.wikipedia.org/wiki/Dm-crypt#Compatibility)



.

---


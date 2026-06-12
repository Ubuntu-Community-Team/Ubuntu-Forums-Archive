---
title: "Triple booted PPC; Can I upgrade the OSX partition?"
date: 2011-11-02
forum: Apple Hardware Users
---

### Post by Chris Grk-O-Matic on 2011-11-02
I have a 1GHz Titanium PowerBook with: OS9, OSX (10.3.9) and Ubuntu, all running nicely. I want to upgrade OSX 10.3.9 to 10.4. 
 
Do you think this will this screw up my existing bootstrap configuration being that I have to boot from the install disk?
 
 
Thanks,
Chris

---

### Post by tiresia on 2011-11-02
> **Chris Grk-O-Matic said:**
> Do you think this will this screw up my existing bootstrap configuration being that I have to boot from the install disk?
Yes, because after installing the MacOSX Installer set Open Firmware to start from the new installed OS.

But this is not a problem. After installing OSX, start pressing the Opt-Key and choose the Linux Partition. When you are in Linux, run ```
ybin -v 
```to update your bootstrap partition.

Before installing MacOSX back up all your data! And you shouldn't use the Tiger Apple Disk Utility if you want to erase the MacOSX partition - if I remember correctly, it would erase the whole HD

---

### Post by Chris Grk-O-Matic on 2011-11-02
Thanks... much appreciated advice :D
 
Chris

---

### Post by Chris Grk-O-Matic on 2011-11-11
I finally got around to doing the upgrade and tiresia's suggestion is not working. This is what I did so far:
 
Performed Panther to Tiger upgrade
 
Rebooted while holding down Option
 
I see 4 radio buttons: OS X - Linux - OS 9 - OS X Install DVD
 
Now, the OS X volume is preselected and I can't select any other volume. I would like to get into Ubuntu to ybin -v as suggested.
 
So I'm guessing there's something wrong with bootstrap?

---

### Post by Chris Grk-O-Matic on 2011-11-11
Whooop disregard my lost post. Seems a few reboots did the trick.
 
I was able to select Ubuntu and do a ybin -v and before long the terminal said I got Blessed with Penguin Pee.
 
Yippee
 
 
Thank you Ubuntu Forum

---


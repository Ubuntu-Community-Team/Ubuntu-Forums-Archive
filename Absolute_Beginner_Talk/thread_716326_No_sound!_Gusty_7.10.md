---
title: "No sound! Gusty 7.10"
date: 2008-03-05
forum: Absolute Beginner Talk
---

### Post by toxicgtr on 2008-03-05
Gidday,

Just installed Ubuntu 7.10, and cant hear a thing when i play my music or when Ubuntu starts up.
When i go into the sound preferences and click "test" next to the Music and movies sound play back it says:

 "audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=music: Could not open resource for writing."

I've installed ALSA but still doesnt work? My soundcard is integrated into the motherboard.

Any ideas?

My specs of my computer:

- AMD 6000+ Dual core 3.0GHZ
- ASUS M2N-E SLI mainboard
- Transcend 4GB DDR2 800MHz Dual Channel Memory
- nVIDIA GeForce 8600GT 512MB DDR3 PCI-E Graphics Accelerator
- Western Digital 400GB 7200RPM 16MB Cache SATA2 Hard Disk Drive
- Asus Quietrack SATA LightScribe Dual Layer DVDRW Drive
- Raidmax Ninja Gaming Tower Case
- Raidmax 520W Power Supply Unit (Intel & AMD Approved)
- Front Audio Connectors (mic/headphones)
- 2 Front / 4 Rear USB 2.0 Connectors
- 2 x 12cm / 1 x 8cm Case Coolers

Cheers!

---

### Post by toxicgtr on 2008-03-05
Bumpin it up!

---

### Post by LuisGMarine on 2008-03-05
paste the output of:
```

sudo lshw -C multimedia

```

---

### Post by toxicgtr on 2008-03-05
Ok,



All it does is show this for about 2 seconds, I've got my sound goin using my headset, but not though my speakers?: 


[img]http://img177.imageshack.us/img177/2385/screenshotev1.png[/img]

---

### Post by toxicgtr on 2008-03-06
Ok, the sounds now working through speakers! WTF! The only thing i did differntly was that command and restarted. Cheers man!

---


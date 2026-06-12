---
title: "can't install tiger over ubuntu"
date: 2005-05-02
forum: Apple PPC Users
---

### Post by jdonnell on 2005-05-02
I installed ubuntu on my ibook earlier this week and my plan was to wipe it and install tiger fresh when I got. I got it today, but I can't get it to boot from the tiger disk. I hold  down 'c' while it's powering up and I get a screen that says to hit c to boot from cdrom or 1 to boot to linux. If I hit 'c' the screen flashes then shows me the same options again. If I do this 3 times it locks up.

---

### Post by slux on 2005-05-02
How about trying to boot from the disc straight from openfirmware by holding down C as the mac boots and makes the sound?

---

### Post by Chunga on 2005-05-02
If that doesn't work for some reason, you can try holding down option at the startup chime.  That will let you select your boot volume at startup.

---

### Post by jdonnell on 2005-05-02
I already tried both. Holding down 'c' is what I described in my first post and holding down 'option' doesn't give me the choice to boot from the cd/dvd. Any other ideas?

---

### Post by jdonnell on 2005-05-02
[QUOTE=slux]How about trying to boot from the disc straight from openfirmware by holding down C as the mac boots and makes the sound?[/QUOTE]

I don't think holding down 'c' boots you into openfirmware. Isn't it 'cmd-opt-O-F

---

### Post by jdonnell on 2005-05-02
I think I got it working. cmd-opt-shift-delete when booting.

---

### Post by slux on 2005-05-02
[QUOTE=jdonnell]I don't think holding down 'c' boots you into openfirmware. Isn't it 'cmd-opt-O-F[/QUOTE]

No, but Open Firmware as opposed to the ubuntu bootloader will boot from the CD-ROM drive if you hold down C IIRC.

---

### Post by jdonnell on 2005-05-02
Ok, I got it to boot from the tiger disk, but the tiger install doesn't show the hard drive when asking for a "destination volume to install" to. Part two of the ubuntu to tiger saga ;)

---

### Post by jdonnell on 2005-05-02
Ok, all is good. I just had to erase the ubuntu partitions

---


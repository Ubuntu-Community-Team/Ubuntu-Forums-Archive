---
title: "Configure default audio input within wine"
date: 2011-04-05
forum: Any Other OS
---

### Post by arkanys on 2011-04-05
Hello, I've been running Linux Mint (KDE, x64) for a couple months now, and have run into an issue I'm having trouble solving with only advice from other threads.

I'm in the process of converting a record collection to digital/cds. I'm using a USB turntable to do so. 

The device shows up fine in the system, and I'm able to record with Audacity. That works fine. However I have a Windows program called "Spin it again" which I find works much better, or more to my liking. However I hate having to reboot into Windows whenever I want to work with them, because that means I'm limited in other areas of work (due to everything being set up in Mint).

So, I've installed Spin it Again in Mint via Wine, but my USB turntable isn't recognized within the program. The only options that show up for selection are 'Default Wave Device', 'default', and 'default'(again).

I'd like help on how to configure Wine so that either my turntable shows up within the program, or the input stream of the turntable to be one of these 'defaults'.

As for specifics, I'm running an Ion turntable on Linux Mint x64  KDE edition (10.10).
Wine v1.2.2-0 with ALSA audio driver
Spin it Again v2.5.43

Thanks for your help!
~Arkanys

---

### Post by davidmohammed on 2011-04-05
if the windows application depends on a USB device, then I'm afraid you are out of luck - wine doesnt (yet) support USB devices.

---

### Post by pricetech on 2011-04-05
You might try windows in a VM.

---

### Post by Perfect Storm on 2011-04-05
Moved to Other OS/Distro Talk Forum.

---


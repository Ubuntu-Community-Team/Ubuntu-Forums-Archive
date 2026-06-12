---
title: "MacBook Pro no sound - Driver Help"
date: 2008-07-23
forum: Apple Hardware Users
---

### Post by da1bu on 2008-07-23
Hi, i recently installed Ubuntu 8.04 on my MacBook Pro and have absolutely no sound. However, i typed lspci -v into the terminal and the system recognizes an audio device but access is denied. It reads:

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
	Subsystem: Apple Computer Inc. Unknown device 00a3
	Flags: bus master, fast devsel, latency 0, IRQ 19
	Memory at db500000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

I've tried looking for drivers for this audio device but there are so many i'm really confused which ones to download. If someone could point to me which drivers need installing / how to get sound on the MacBook pro that would be great.

Thanks.

---

### Post by cyberdork33 on 2008-07-23
Please determine the version of your Macbook pro (It should be version 4 if it is new) and use the appropriate linked guide.

[https://help.ubuntu.com/community/MacBookPro](https://help.ubuntu.com/community/MacBookPro)
[https://wiki.ubuntu.com/MacBookPro/SantaRosa](https://wiki.ubuntu.com/MacBookPro/SantaRosa)
[https://wiki.ubuntu.com/MacBookPro/Penryn](https://wiki.ubuntu.com/MacBookPro/Penryn)

---

### Post by da1bu on 2008-07-23
Thanks for replying. I've followed the instructions (penryn MacBook Pro) and still no sound.

Here are my volume control preferences:

HDA Intel (Alsa mixer)
Master

Do i need to tick any visible tracks or change the volume control preferences?

---

### Post by cyberdork33 on 2008-07-23
> **da1bu said:**
> Thanks for replying. I've followed the instructions (penryn MacBook Pro) and still no sound.

Here are my volume control preferences:

HDA Intel (Alsa mixer)
Master

Do i need to tick any visible tracks or change the volume control preferences?
run 'alsamixer' in the terminal and make sure that the master and PCM channels are unmuted and turned up. If that doesn't work try other channels as well.

---

### Post by da1bu on 2008-07-24
Thanks, got it working. Great support again cyberdork.

---

### Post by kdb424 on 2008-07-24
> **cyberdork33 said:**
> Please determine the version of your Macbook pro (It should be version 4 if it is new) and use the appropriate linked guide.

[https://help.ubuntu.com/community/MacBookPro](https://help.ubuntu.com/community/MacBookPro)
[https://wiki.ubuntu.com/MacBookPro/SantaRosa](https://wiki.ubuntu.com/MacBookPro/SantaRosa)
[https://wiki.ubuntu.com/MacBookPro/Penryn](https://wiki.ubuntu.com/MacBookPro/Penryn)

With the amount of times you post that, just put that in your signature, and tell people look down. lol.

---

### Post by cyberdork33 on 2008-07-24
> **kdb424 said:**
> With the amount of times you post that, just put that in your signature, and tell people look down. lol.
I've already got other important info down there, and I am quite limited on space. I should add a section to the FAQ that explains this for everyone...

---


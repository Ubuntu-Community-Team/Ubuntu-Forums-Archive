---
title: "No bass with Intel iMac 7,1 - I've tried so many things!"
date: 2009-08-11
forum: Apple Hardware Users
---

### Post by Litropy on 2009-08-11
My iMac has only two speakers, and I am not using external speakers. When I boot into OS X, the audio is rich, full of bass, and everything I expect. When I boot into Jaunty, I get no bass. Please note: there is no subwoofer in this machine! [http://www.everymac.com/systems/apple/imac/stats/imac-core-2-duo-2.4-20-inch-aluminum-specs.html](http://www.everymac.com/systems/apple/imac/stats/imac-core-2-duo-2.4-20-inch-aluminum-specs.html)

The line I used to **configure alsa-driver, alsa-lib, and alsa-utils** is:
```
sudo ./configure --with-kernel=/usr/src/linux-headers-$(uname -r) --with-cards=hda-intel --with-oss=yes
```


I downloaded the latest alsa-driver, alsa-lib, and alsa-utils and installed without error. **cat /proc/asound/version returns:** 

```
Advanced Linux Sound Architecture Driver Version 1.0.20.
Compiled on Aug 10 2009 for kernel 2.6.28-14-generic (SMP).
```

Furthermore, **uname -a**

```
Linux Litropy 2.6.28-14-generic #47-Ubuntu SMP Sat Jul 25 01:19:55 UTC 2009 x86_64 GNU/Linux
```

**sudo dmidecode -s system-product-name**

```
iMac7,1
```

**lspci | grep -i audio**

```
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
```

**head /proc/asound/card0/codec#0**

```
Codec: Realtek ALC889A
Address: 0
Function Id: 0x1
Vendor Id: 0x10ec0885
Subsystem Id: 0x106b3000
Revision Id: 0x100103
No Modem Function Group found
Default PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
```

For **sudo gedit /etc/modprobe.d/alsabase.conf** , I have tried just about every model within the guide at [http://ubuntuforums.org/showthread.php?t=611345&highlight=imac+7%2C1](http://ubuntuforums.org/showthread.php?t=611345&highlight=imac+7%2C1)

**Currently**, it is set to:
```
options snd-hda-intel model=asus-a7m
```

... and that setting has always been the only line within alsabase.conf

**/home/litropy/.asoundrc** just has the include for .asoundconf - no custom settings there.

I have tried adjusting various volume sliders. As of the driver update, there is no more clipping (crackling). And once again, after all this, I still have no bass. Please help me out.

---

### Post by Litropy on 2009-08-12
bump. As far as I can tell, OS X does not have a system-wide EQ. I've asked #macdev, and they know nothing of it. And, a Google search reveals nothing, either.

Please help, guys - I've been trying to find a solution to this problem for a couple of months now.

---


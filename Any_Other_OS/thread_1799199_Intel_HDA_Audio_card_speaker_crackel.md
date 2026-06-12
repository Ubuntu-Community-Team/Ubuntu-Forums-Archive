---
title: "Intel HDA Audio card speaker crackel"
date: 2011-07-07
forum: Any Other OS
---

### Post by aman524 on 2011-07-07
I just did a clean install of Ubuntu 11.04 on my Compaq Presario C700. The first thing I noticed is that the speakers have a strange white noise like sound coming out of them when they are not playing any audio. It sounds like they "turn on and off" when I play audio with loud pop. I can't seem to figure out what the problem is!

lspci output:
```
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
	Subsystem: Hewlett-Packard Company Device 30d9
	Flags: bus master, fast devsel, latency 0, IRQ 43
	Memory at 92400000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit+
	Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
	Capabilities: [100] Virtual Channel
	Capabilities: [130] Root Complex Link
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

```

---

### Post by lidex on 2011-07-08
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by aman524 on 2011-07-08
> **lidex said:**
> Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]
It would not upload the output so I had it output to a file and will attach it here to this post.

---

### Post by lidex on 2011-07-08
I thought you said you installed ubuntu, looks like mint to me. What is this output:
```
dpkg -l | grep "alsa"
```

---

### Post by Perfect Storm on 2011-07-09
Moved to Other OS/Distro Talk.

---

### Post by aman524 on 2011-07-09
> **lidex said:**
> I thought you said you installed ubuntu, looks like mint to me. What is this output:
```
dpkg -l | grep "alsa"
```

sorry about that,
here's the output
```
ii  alsa-base                             1.0.24+dfsg-0ubuntu1                       ALSA driver configuration files
ii  alsa-utils                            1.0.24.2-0ubuntu6                          Utilities for configuring and using ALSA
ii  bluez-alsa                            4.91-0ubuntu1                              Bluetooth ALSA support
ii  gstreamer0.10-alsa                    0.10.32-1ubuntu5                           GStreamer plugin for ALSA

```

---

### Post by lidex on 2011-07-09
OK, probably should have asked for this ```
dpkg -l | grep "asound"
```

---

### Post by aman524 on 2011-07-09
> **lidex said:**
> OK, probably should have asked for this ```
dpkg -l | grep "asound"
```

Here's the output:
```
ii  libasound2                            1.0.24.1-0ubuntu5
     shared library for ALSA applications
ii  libasound2-plugins                    1.0.24-0ubuntu2
     ALSA library additional plugins

```

---

### Post by lidex on 2011-07-09
Try installing this:
```
sudo apt-get install lib32asound2
```

---

### Post by aman524 on 2011-07-09
> **lidex said:**
> Try installing this:
```
sudo apt-get install lib32asound2
```

E: Unable to locate package lib32asound2
When I look up the package to install it manually I can only find an amd64 version, which is not my architecture.

---

### Post by lidex on 2011-07-09
OK then, kind of a shot in the dark. You do have an issue with your alsa libs so the next step would be an alsa re-install:
Using a Terminal="Applications->Accessories->Terminal"
```
sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2
```
**Reboot.**

For a 'command not found' error simply install aptitude:
```
sudo apt-get install aptitude
```

---

### Post by aman524 on 2011-07-09
sorry still did not fix the problem... I'm baffled by this.

---

### Post by lidex on 2011-07-09
Let's look at your updated alsa-info.
See this post:
[http://ubuntuforums.org/showpost.php?p=11031344&postcount=4](http://ubuntuforums.org/showpost.php?p=11031344&postcount=4)

---


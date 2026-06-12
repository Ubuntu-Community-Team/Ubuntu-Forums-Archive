---
title: "nvidia driver question"
date: 2007-12-13
forum: Absolute Beginner Talk
---

### Post by howie78 on 2007-12-13
I am having some difficulty getting visual effects to enable. I enabled the restricted driver for the nvidia card and it still doesn't allow me to enable visual effects. I ran the command to identify the card. here is what I got:

 lspci | grep VGA
01:00.0 VGA compatible controller: nVidia Corporation NV10DDR [GeForce 256 DDR] (rev 10)

Let me know if you all need other information. I am working on the solution myself. Its  bit older card so that maybe the issue with lack of avaliable driver but I just wanted to play the visual effects. Other than that I am loving my new exploration into the ubuntu world.

Thanks,
Howard

---

### Post by FuturePilot on 2007-12-13
Can you post the output of 
```
compiz --replace
```

---

### Post by Pumalite on 2007-12-13
Your graphics might not support it.

---

### Post by howie78 on 2007-12-13
> **FuturePilot said:**
> Can you post the output of 
```
compiz --replace
```

here you go:

 compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0101 (rev 10) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity

---

### Post by FuturePilot on 2007-12-13
> **howie78 said:**
> here you go:

 compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0101 (rev 10) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity

Do you know which driver you are using?
If you don't this will tell
```
cat /proc/driver/nvidia/version
```

Sorry, should have asked for that earlier ;)

---

### Post by howie78 on 2007-12-13
> **FuturePilot said:**
> Do you know which driver you are using?
If you don't this will tell
```
cat /proc/driver/nvidia/version
```

Sorry, should have asked for that earlier ;)

Here you go:

 cat /proc/driver/nvidia/version
NVRM version: NVIDIA Linux x86 Kernel Module  1.0-7185  Mon Apr  2 18:29:54 PDT 2007
GCC version:  gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)

---

### Post by FuturePilot on 2007-12-13
Yes, unfortunately that driver doesn't support compositing. Not much can be done about that. Unless you try installing xserver-xgl, but I'm not sure how much success you will have with it.
:(

---

### Post by howie78 on 2007-12-13
> **FuturePilot said:**
> Yes, unfortunately that driver doesn't support compositing. Not much can be done about that. Unless you try installing xserver-xgl, but I'm not sure how much success you will have with it.
:(

Ahh kinda suspected that was the issue. Its just a older PC I am using to fool around with ubuntu on. No biggie I can still use ubuntu just can't play with the flashy visual toys. Thanks for the rapid responses and help though!

---


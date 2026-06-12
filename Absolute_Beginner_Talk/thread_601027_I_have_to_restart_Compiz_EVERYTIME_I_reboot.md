---
title: "I have to restart Compiz EVERYTIME I reboot??"
date: 2007-11-02
forum: Absolute Beginner Talk
---

### Post by Tdukes on 2007-11-02
If I dont restart it./.....I get no graphic effects....whats the deal


heres the restart log

Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0091 (rev a1) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (2880x900) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
/usr/bin/compiz.real (core) - Warn: Unknown option '--restart'

---

### Post by djchandler on 2007-11-02
> **Tdukes said:**
> If I dont restart it./.....I get no graphic effects....whats the deal


heres the restart log

Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0091 (rev a1) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (2880x900) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
/usr/bin/compiz.real (core) - Warn: Unknown option '--restart'

What GPU is on your NVidia card and which restricted driver are you using?
I'm having trouble getting any Open GL support at all on an old GeForce 2 MX 200 using the nvidia-glx-legacy driver with Gutsy. It had no troubles in Feisty. Looks like you have a similar problem. Still trying to figure out what I did wrong, and I did a fresh install. You're not the only one having trouble with compiz either. I know of someone having a problem with a GeForce 7 pci-e series card too. Makes me wonder if compromises were made to get ATI drivers to work right in Gutsy.

DJ

---


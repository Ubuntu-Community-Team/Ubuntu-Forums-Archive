---
title: "Strange Wireless and 686 kernel hang-time"
date: 2006-07-19
forum: Absolute Beginner Talk
---

### Post by unconquerable on 2006-07-19
I currently have (2) problems which may force me to use windows if I cannot get them fixed.  I just bought a pc after using a mac for 3 years.

[SIZE="4"]_**Problem 1:  Wireless**_[/SIZE]

I installed network-manager it does not recognize any networks even though there is wireless network in the air, and connected to by the normal networking program.

When connected to the wireless network manuelly (typing in SSID and  Channel), I attempt to go to websites and it hangs at half way loaded or does not load at all.  Very rarely do I actually see data that has loaded.  GAIM won't connect either. ](*,) 

(WEIRD PART) I can still download full speed (60 kbps) in synaptic package manager, I did all my updates wirelessly.  

[SIZE="4"]_**Problem 2:  686 Kernel smp**_[/SIZE]

I updated to the 686 Kernel smp through Synaptic and now when I boot the computer hangs for 45 seconds at the mounting root filesystem before continuing.  Why is this happening, it did not with the 386 kernel.

---

### Post by Metacarpal on 2006-07-19
Not sure how to fix your #1, but I have a thought on #2...

What processor are you running?  The SMP packages are for Symmetric Multi-Processing - meaning, having more than one processor in the unit.  If you're running a regular 686 processor, like a Pentium III, you'll want to install the regular (non-SMP) 686 packages and uninstall the SMPs.

---

### Post by unconquerable on 2006-07-19
I am running an Intel Core Duo.  Also, the wireless did work in firefox semi well before installing the 686 kernel.

---

### Post by unconquerable on 2006-07-19
I went back to the 386 kernel, it still downloads packages, but not websites.  I am totally lost here.

---

### Post by MarkSheely on 2006-07-19
What kind of wireless card do you have?

---

### Post by unconquerable on 2006-07-19
> **MarkSheely said:**
> What kind of wireless card do you have?

Intel PRO/Wireless 3945ABG card in a HP DV2000t.

---


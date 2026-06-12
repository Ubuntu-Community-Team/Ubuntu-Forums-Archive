---
title: "correct intel driver?"
date: 2007-05-22
forum: Absolute Beginner Talk
---

### Post by locke.dragon on 2007-05-22
[IMG]http://i159.photobucket.com/albums/t147/clipsandeggs/Screenshot-6.png[/IMG]

how can i tell which card i have?  and then how can i make sure i have the right driver installed?  thanks in advance.  :D

---

### Post by taurus on 2007-05-22
Applications -> Accessories -> Terminal
```
lspci
```

---

### Post by locke.dragon on 2007-05-22
```

link@aperturescience:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03)
02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
02:01.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832
02:01.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
02:01.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)
02:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
02:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
02:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
link@aperturescience:~$ 

```

---

### Post by taurus on 2007-05-22
Here's your graphic card.

```
00:02.0 VGA compatible controller: **Intel Corporation Mobile 915GM/GMS/910GML** Express Graphics Controller (rev 03)
```

---

### Post by veloce on 2007-05-23
> **locke.dragon said:**
> [IMG]http://i159.photobucket.com/albums/t147/clipsandeggs/Screenshot-6.png[/IMG]

how can i tell which card i have?  and then how can i make sure i have the right driver installed?  thanks in advance.  :D

So the answer to your original question is that you have the "intel" driver installed and, yes, that is the correct driver for your system.  You can also use the "i810" driver.

Based on what I've learned in the last couple of days: the "intel" driver is an upgrade from the "i810".  The only issue with the intel driver is that it is more difficult (read: REALLY difficult if not IMPOSSIBLE) to get dual monitors working.

The "intel" driver also eliminates the need to install "915resolution" - so don't listen if you get told to install that.

EDIT: oops, you also have the i740 installed.  Hopefully you are using the "intel" driver not the "i740".  To check this, you need to have a look at your /etc/X11/xorg.conf file.  In the "device" section, check that the driver is "intel" not "i740".

---

### Post by ggaaron on 2007-05-23
When you have i810 driver your also don't need any tools for changing your resolution, I don't know why would you need it? Everything works well, you can use i810, and you can use intel, they are booth compatible with your graphics card, but from my experience it's better to use i810 - with intel driver resolutions didn't work as they should - I have a wide screen and every resolution was stretched to match it, even if it was a "normal" resolution, there are also problems with beryl on it, so I really recommend i810.

Don't forget to change your driver in /etc/X11/xorg.conf after installing new driver and restart your X server. Good luck=)

---

### Post by ggaaron on 2007-05-23
> **veloce said:**
> 
The "intel" driver also eliminates the need to install "915resolution" - so don't listen if you get told to install that.

I'm really curious, what do I have to do to have to install 915resolution? You know, I've never used it, I own two computers with Ubuntu that can change resolutions perfectly and I can't see the point of existence of 915resolution. Can someone explain it to me?=)

---

### Post by veloce on 2007-05-23
> **ggaaron said:**
> I'm really curious, what do I have to do to have to install 915resolution? You know, I've never used it, I own two computers with Ubuntu that can change resolutions perfectly and I can't see the point of existence of 915resolution. Can someone explain it to me?=)

There's a full description of 915resolution on it's website.  Briefly: 
If you only use "standard" resolutions then you wont need to worry about 915resolution.  My laptop screens native resolution is 1400x1050 i.e. not standard. To allow this mode to be set the 915resolution hacks the video bios to add it to the list.

Mode setting has been added to the "intel" driver to eliminate the need for 915resolution as a separate package.

---

### Post by ggaaron on 2007-05-24
Now I can see this, thanks for explanation.

---

### Post by .adma on 2007-05-24
> **ggaaron said:**
> When you have i810 driver your also don't need any tools for changing your resolution, I don't know why would you need it? Everything works well, you can use i810, and you can use intel, they are booth compatible with your graphics card, but from my experience it's better to use i810 - with intel driver resolutions didn't work as they should - I have a wide screen and every resolution was stretched to match it, even if it was a "normal" resolution, there are also problems with beryl on it, so I really recommend i810.

Don't forget to change your driver in /etc/X11/xorg.conf after installing new driver and restart your X server. Good luck=)

I am going to disagree with this (at least as a solution for all supposed-supported cards).  I have the 915GM chipset and 810 would not work for anything, even with 915resolution.  I installed the intel driver and enjoyed instant success!

---

### Post by .adma on 2007-05-24
> **locke.dragon said:**
> [IMG]http://i159.photobucket.com/albums/t147/clipsandeggs/Screenshot-6.png[/IMG]

how can i tell which card i have?  and then how can i make sure i have the right driver installed?  thanks in advance.  :D

Also, I am really new :)  Can you tell me where that driver repository is, that he has a SS of there?  Thanks!

---

### Post by veloce on 2007-05-24
> **.adma said:**
> Also, I am really new :)  Can you tell me where that driver repository is, that he has a SS of there?  Thanks!

That is a Synaptic Package Manager screen. As a graphical tool, it's pretty self explanatory.

---

### Post by .adma on 2007-05-24
i didnt recognize it because I have been using the add/remove feature under applications.  They appear to be linked to same lists. whats the difference?

---

### Post by veloce on 2007-05-24
> **.adma said:**
> i didnt recognize it because I have been using the add/remove feature under applications.  They appear to be linked to same lists. whats the difference?

They are both just different front ends to "apt", Ubuntu's package manager.  Use whichever is easiest for the task at hand.  Synaptic is package focussed, "add/remove under applications is application focussed.  Horses for courses.

---

### Post by Seeker84 on 2007-05-25
> **ggaaron said:**
> I'm really curious, what do I have to do to have to install 915resolution? You know, I've never used it, I own two computers with Ubuntu that can change resolutions perfectly and I can't see the point of existence of 915resolution. Can someone explain it to me?=)

some i810 drivers need a resolution fix, the driver fixed my resolution perfectly

---


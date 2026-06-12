---
title: "No desktop effects!!! :-("
date: 2007-07-31
forum: Absolute Beginner Talk
---

### Post by ehubu on 2007-07-31
Every time I open the desktop effects [System>Preferences>Desktop Effects] a message appears: "Composite extension isn't enabled", I've looked over the forum for this topic, the only one I found was too difficult to me to understand. If i have to enter to the terminal program please tell me all the steps i have to do, because I'm new here on Ubuntu and i don't know absolutely nothing, but I  really enjoy Ubuntu.

Thanks very much for your help, (Scuse my bad English)

---

### Post by wolfen69 on 2007-07-31
did you install the proper drivers for your video card?

---

### Post by Ek0nomik on 2007-07-31
What video card do you have?

If you don't know, open a terminal and type:

```
lspci
```

That should reveal it for you.

---

### Post by ehubu on 2007-07-31
erik@erik-ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub
00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.4 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 5 (rev 01)
00:1c.5 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 6 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GH (ICH7DH) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 SATA controller: Intel Corporation 82801GR/GH (ICH7 Family) Serial ATA Storage Controller AHCI (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc RV380 [Radeon X600 (PCIE)]
01:00.1 Display controller: ATI Technologies Inc RV380 [Radeon X600]
04:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller (rev 01)

---

### Post by Motoxrdude on 2007-07-31
You have to create a xgl session.
Here is a good tutorial: [http://ubuntuforums.org/showthread.php?t=481314&highlight=xgl+ati]("http://ubuntuforums.org/showthread.php?t=481314&highlight=xgl+ati")
With this you are going to be using compiz-fusion. It has a lot more features then the desktop-effects.

---

### Post by ehubu on 2007-07-31
thanks very much!

---

### Post by Motoxrdude on 2007-07-31
Yeah no problem. Let me know how it goes.

---


---
title: "ubunto extra visual effects not working on HP pavillion 6629 with intel graphic card"
date: 2008-02-19
forum: Absolute Beginner Talk
---

### Post by jebasan on 2008-02-19
Hi everyone,

I've just installed ubuntu in my laptop a few days ago and everything works just fine. but the extra visual effects does not load and gives me this messege "desktop effect could no be enable".

also my sound and mic (integraded) does'n work.

I have a intel graphic media accelerator x3100 - 2gb of memory and large hd 250 (shared with widows vista Shi....t. 

here the code: (lspci)

[B]00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)[/B]

00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
02:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
07:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
07:09.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
07:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
07:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
07:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)

i've beign reading the forums but i haven't find some answers yet. 
Can somebody help?

---

### Post by superprash2003 on 2008-02-19
you can try fixing the sound by going to system-preferences-sound and manually change the values for sound playback,sound capture from auto detect to the ones present.. It is like trial and error.. CS46XX worked for me..

cheers!!

---

### Post by jebasan on 2008-02-19
hi again,

i've tried that but nothing. the optons i have under the pull down menu are: autodetect, SI3050 modem, HDA generic, Alsa adv. linux.... , ESD and OSS. none of them does nothing .
under the ESD i have some error message: audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not establish connection to sound server

thanks again.

---

### Post by Golem XIV on 2008-02-19
Take a look at my reply to [this post]("http://ubuntuforums.org/showthread.php?t=695195") for the Intel 965/X3100 issues.

---

### Post by Hobo Joe on 2008-02-19
What you need to do for sound is this, first, run this command:
```

sudo asoundconf list

```
That will give you a list of different sound cards, find the card on the list that is the one you want to use, then run this command:
```

sudo asoundconf set-default-card [card name]

```

Hope that works!

---

### Post by jebasan on 2008-02-19
Hi Hobo Joe,

I've did the code you send us but nothing yet. The good thing [ correct me if i'm wrong ] is the i didn't recieve any error message. But no sound yet.

---


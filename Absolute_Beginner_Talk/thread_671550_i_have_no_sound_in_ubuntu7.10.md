---
title: "i have no sound in ubuntu7.10"
date: 2008-01-18
forum: Absolute Beginner Talk
---

### Post by pmn.blazer on 2008-01-18
hello in my compaqV6000 there is no sound...
but window vista is ok to run the sound..pls help me
this is the output of **lspci**
[HTML]00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 **Audio device**: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
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
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
07:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
07:09.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
07:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
07:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
07:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)[/HTML]
and this is my **alsamixer** this is i attache of it

---

### Post by Aurora@FleetBuzz on 2008-01-18
You may have to adjust your settings in alsamixer.  There is more to alsamixer than just the screenshot you posted.  Use the right arrow (-->) key to see more choices.  Here's a thread that helped me with a sound problem.
[http://ubuntuforums.org/showthread.php?t=655642](http://ubuntuforums.org/showthread.php?t=655642)

---

### Post by pmn.blazer on 2008-01-18
no fri...In my laptop..i can't hear both external speaker and earphone at all...
so...i don't know why is it??in ubuntu 7.10

---

### Post by Aurora@FleetBuzz on 2008-01-18
Yes, I understand you have no sound.  But I suggest you go into alsamixer and enable all the settings and turn up the volumes to maximum.  Just make sure you write down the settings before you change them in case you have to set them back!  Try the sound after enabling each one.  I am not saying this will work, but it might....

See post #5 on this thread for instructions on how to adjust settings in alsamixer.  Good luck.
[http://ubuntuforums.org/showthread.php?t=648381&highlight=headphones](http://ubuntuforums.org/showthread.php?t=648381&highlight=headphones)

---

### Post by pmn.blazer on 2008-01-18
hello I don't understand clearly of it..pls hint me more...

---

### Post by pmn.blazer on 2008-01-18
[http://ubuntuforums.org/showthread.php?t=314383](http://ubuntuforums.org/showthread.php?t=314383)

reference of this 
i don't know my model how can i see it??
I just know that i am using compaq v6560EA....

options snd-hda-intel model=xyz

so...what can i add in xyz??

---

### Post by limac on 2008-01-18
pmn.blazer; upgrade to the latest version of alsa 
first off, what sound card do you have?

---

### Post by pmn.blazer on 2008-01-18
yes i think i do not need update of it cause** my alsamixer** is
[HTML]&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;[AlsaMixer v1.0.14 (Press Escape to quit)]&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
&#9474; Card: HDA Intel                                                              &#9474;
&#9474; Chip: Realtek ID 268                                                         &#9474;
&#9474; View: [Playback] Capture  All                                                &#9474;
&#9474; Item: Master [dB gain=0.00, 0.00]                                            &#9474;
&#9474;                                                                              &#9474;
&#9474;           &#9484;&#9472;&#9472;&#9488;             &#9484;&#9472;&#9472;&#9488;                                              &#9474;
&#9474;           &#9474;&#9618;&#9618;&#9474;             &#9474;&#9618;&#9618;&#9474;                                              &#9474;
&#9474;           &#9474;&#9618;&#9618;&#9474;             &#9474;&#9618;&#9618;&#9474;                                              &#9474;
&#9474;           &#9474;&#9618;&#9618;&#9474;             &#9474;&#9618;&#9618;&#9474;                                              &#9474;
&#9474;           &#9474;&#9618;&#9618;&#9474;             &#9474;&#9618;&#9618;&#9474;                                              &#9474;
&#9474;           &#9474;&#9618;&#9618;&#9474;             &#9474;&#9618;&#9618;&#9474;                                              &#9474;
&#9474;           &#9474;&#9618;&#9618;&#9474;             &#9474;&#9618;&#9618;&#9474;                                              &#9474;
&#9474;           &#9474;&#9618;&#9618;&#9474;             &#9474;&#9618;&#9618;&#9474;                                              &#9474;
&#9474;           &#9474;&#9618;&#9618;&#9474;             &#9474;&#9618;&#9618;&#9474;                                              &#9474;
&#9474;           &#9474;&#9618;&#9618;&#9474;             &#9474;&#9618;&#9618;&#9474;                                              &#9474;
&#9474;           &#9474;&#9618;&#9618;&#9474;             &#9474;&#9618;&#9618;&#9474;                                              &#9474;
&#9474;           &#9474;&#9618;&#9618;&#9474;             &#9474;&#9618;&#9618;&#9474;                                              &#9474;
&#9474;           &#9492;&#9472;&#9472;&#9496;             &#9492;&#9472;&#9472;&#9496;             &#9484;&#9472;&#9472;&#9488;             &#9484;&#9472;&#9472;&#9488;            &#9474;
&#9474;                                             &#9474;MM&#9474;             &#9474;MM&#9474;            &#9474;
&#9474;                                             &#9492;&#9472;&#9472;&#9496;             &#9492;&#9472;&#9472;&#9496;            &#9474;
&#9474;         100<>100         100<>100                                            &#9474;
&#9474;        < Master >          PCM            Caller I         Off-hook          &#9474;
&#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;

[/HTML]

pls i really really eager to get sound from ubuntu

---

### Post by BandD on 2008-01-18
It looks like the best solution for you will be to upgrade the ALSA driver to version 1.0.15.  If you look here: [https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller]("https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller")

at Method B is says this will fix the problem for a Compaq V6000.  There is also a short guide for what you need to do to install the new driver.  Here is the code from that page:
```

wget ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15rc1.tar.bz2
tar xvpjf alsa-driver-1.0.15rc1.tar.bz2
cd alsa-driver-1.0.15rc1
./configure --with-cards=hda-intel
make
sudo make install
```

Type each line into the terminal one at a time.  You can also copy and paste.  To paste in the Terminal you need to press Ctrl+Shift+V.

I hope this helps you.

---


---
title: "Help-swap advice for wife"
date: 2006-07-07
forum: Absolute Beginner Talk
---

### Post by dazzler on 2006-07-07
Can anyone please help me with two things, the solver gets a full night with the missus :)

Only been using Ubuntu and indeed linux for a week but i cannot for the life of me get my Nebula PCI card working, and tbh dont know where to start, im running 32 bit ubuntu on AMD Athlon 3000+

This is the error when trying tvtime from terminal

```
Running tvtime 1.0.1.
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/dazzler/.tvtime/tvtime.xml
videoinput: Can't get tuner info: Invalid argument
videoinput: Can't get tuner info: Invalid argument

```

This is what i get from lspci from terminal

```
dazzler@ubuntu:~$ lspci
0000:00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
0000:00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a3)
0000:00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
0000:00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
0000:00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
0000:00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev a2)
0000:00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev a3)
0000:00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev a3)
0000:00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2)
0000:00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
0000:00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
0000:00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
0000:00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
0000:00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Hyp erTransport Technology Configuration
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Add ress Map
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRA M Controller
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Mis cellaneous Control
0000:01:06.0 FireWire (IEEE 1394): NEC Corporation uPD72874 IEEE1394 OHCI 1.1 3- port PHY-Link Ctrlr (rev 01)
0000:01:07.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capt ure (rev 11)
0000:01:07.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (r ev 11)
0000:01:08.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07 )
0000:01:08.1 Input device controller: Creative Labs SB Live! MIDI/Game Port (rev  07)
0000:05:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600 GT ] (rev a2)
dazzler@ubuntu:~$

```

The other niggle i have is, i have to manually deactivate then activate my network card to get onto the internet, i think i dorked something when i tried a tip on these forums to speed browsing up ip4 and all that

Cheers

Will supply photo of wife if needed to potential gurus :mrgreen:

---

### Post by steve.horsley on 2006-07-07
I found this. Don't know if it will help.
[http://www.nebula-electronics.com/support/developers.asp](http://www.nebula-electronics.com/support/developers.asp)

---

### Post by dazzler on 2006-07-07
Thanks but thats way over my head, may as well be russian to me.

I thought ubuntu came with the bttv and dvb drivers pre-installed if so how do i apply the patch on the link you kindly provided.

Thnks in advance

---

### Post by dazzler on 2006-07-07
[IMG]http://ejmas.com/pt/2004pt/tisha/training.jpg[/IMG]

Heres the missus any more offers ;)

---

### Post by Stew2 on 2006-07-07
> **dazzler said:**
> [IMG]http://ejmas.com/pt/2004pt/tisha/training.jpg[/IMG]

Heres the missus any more offers ;)

:D Wow! :D  What the heck are you doing farting around with computers for? :mrgreen:

P.S. Sorry I cant help out!

---

### Post by dazzler on 2006-07-07
Shes always at the gym lol ](*,)

---

### Post by deanlinkous on 2006-07-07
Where do you live...I am on the way!

---


---
title: "sound test"
date: 2008-03-21
forum: Absolute Beginner Talk
---

### Post by jtmedin on 2008-03-21
ok i give up how does one test the sound card. It played when i started but what do i do to  check again for sound? TIA

---

### Post by st33med on 2008-03-21
You are coming from Windows, which, I presume, is really noisy with BEEPs and piano keys. Ubuntu is usually very silent until it needs to play sound. Just try YouTube for sound.

Or, if I am wrong, please give us the output from:
```
lspci
```

in the terminal. The terminal is in Applications>>Accessories.

---

### Post by herbster on 2008-03-21
To test your sound card itself, use speaker-test. Which card do you have and how many speakers? A default test would be something like

```
speaker-test -twav
```

Just tests the front left. To check the default device for front left/right do:

```
speaker-test -twav -c2 -Ddefault
```

---

### Post by spiderbatdad on 2008-03-21
> **herbster said:**
> To test your sound card itself, use speaker-test. Which card do you have and how many speakers? A default test would be something like

```
speaker-test -twav
```

Just tests the front left. To check the default device for front left/right do:

```
speaker-test -twav -c2 -Ddefault
```

Ctrl-c to escape that.

---

### Post by forrestcupp on 2008-03-21
> **herbster said:**
> To test your sound card itself, use speaker-test. Which card do you have and how many speakers? A default test would be something like


Sweet.

---

### Post by herbster on 2008-03-21
Ah yes, ctrl+c. May not want it going on forever ;) :D

---

### Post by jtmedin on 2008-03-29
lspci
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX 4000] (rev c1)
02:01.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
02:02.0 Ethernet controller: 3Com Corporation 3c940 10/100/1000Base-T [Marvell] (rev 12)
02:04.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
02:07.0 Communication controller: Conexant HSF 56k Data/Fax/Voice/Spkp (w/Handset) Modem (rev 01)

---

### Post by herbster on 2008-03-29
jtmedin, Try the command I posted a few posts up.

---

### Post by jtmedin on 2008-03-31
tried: speaker-test -twav
& got no sound

Went to preferences -> sound & was unable to get any sound

---

### Post by jtmedin on 2008-04-03
Ok i have no sound what do i do to reinstall? TIA

---

### Post by herbster on 2008-04-04
We have missed checking your mixer. Run "alsamixer" and ensure the mixer levels are unmuted and set high enough or to full. Then run the speaker-test again.

Also, paste the output of

```
modinfo soundcore
```

---


---
title: "Dual 500Mhz G4 ATI Card X Server Problem"
date: 2007-05-21
forum: Apple PPC Users
---

### Post by leoos on 2007-05-21
Im trying to install Ubuntu 7 (and have also failed with 6 also) on a Power Mac G4 Gigabit Ethernet Dual 500Mhz G4 (I didnt realise that these are almost 7 years old now). Its got an ATI RAGE Card (ATI RAGE 128 Pro graphics card with 16MB of SDRAM graphics memory installed in a dedicated AGP 2X graphics slot)

My problem is that the X Server fails to launch in both the installer (Iended up using the alternate installer) and after installing. Now Im not at the machine right now as its at home and Im at work but its a framebuffer issue if I remember correctly, it basically goes to a blue screen and says it fails to start the X environment. I tried manually reconfiguring it and editing colour depths as suggested in some posts here but am still drawing a blank. 

Im hoping someone might have some experience with the ATI RAGE and PPC Ubuntu that could maybe help me out a little. Thanks in advance.

---

### Post by stmiller on 2007-05-21
Can you post the entire /etc/X11/xorg.conf here?

And post the output of the log file

/var/log/Xorg.0.log

not the whole thing, just lines that have

(EE) 

errors

---

### Post by Arothian on 2007-05-27
I'm having similar problems on a Dual 876mhz G4 with a ATI Rage 128 (not pro) video card. I don't particularly want to type out the whole config file. Here are some parts.

```

Section "Device"
            Identifier    "ATI Technologies Inc Rage 128 RE/SG"
            Driver         "ati"
            BusID         "PCI:10:13.0"
            Option       "UseFBDev"                  "false"
EndSection

Section "Monitor"
          Identifier     "DELL 1907FP"
          Option         "DPMS"
          HorizSync    30-65 
          VertRefresh  50-75
EndSection

```

The errors:
(II) ATI: Candidate "Device" section "ATI Technologies Inc Rage 128 RE/SG".
(EE) No Devices detected.

Fatal server error:
no screens found


I've tried manually reconfiguring the xserver. 
lspci gives me

0001:10:13.0 for my video card location, so I'm using 10:13.0 as PCI location

I've tried "UseFBDev" with both false and true setting.

---

### Post by stmiller on 2007-05-27
This is a long shot guess, but try setting the driver to

Driver      "r128"

and put in a line in the Device section that says

Option "AGPMode" "2"

---

### Post by EuroCity on 2007-05-28
I have the same problem with Ubuntu 7.04 and my trusted (albeit "old") Power Mac G4 AGP, with a Radeon 9000 Mac Edition video card: incredibly, the X server fails to start; this never happened before with any stable Ubuntu version!

The only option, sofar, has been to use the

```
live video=ofonly
```

option with the Desktop CD, and the

```
quiet splash video=ofonly
```

option in */etc/yaboot.conf*: essentially, just add *video=ofonly*, and everything should work, at least until the problem is fixed.

BTW, with the Radeon 9000 (on a DVI connection) there is still a problem with colour corruption until one changes resolution forth and back (and there was also a post here about this still unsolved problem, some months ago); see also here, for example (apparently, very few people have reported this bug):

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/35724](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/35724)

---

### Post by EuroCity on 2007-05-30
^^^ FYI, problem solved (at least for my configuration); just see the - updated - link above again:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/35724](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/35724)

---

### Post by Arothian on 2007-06-01
I tried setting the driver to 'r128' which didn't help. The Rage 128 card I'm using is PCI not AGP.

---


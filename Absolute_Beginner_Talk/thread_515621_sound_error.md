---
title: "sound error"
date: 2007-08-02
forum: Absolute Beginner Talk
---

### Post by Nolander on 2007-08-02
i get a error when i lanch totem player
```
The requested audio output was not found. Please select another audio output in the Multimedia Systems Selector.
```
where do i find the Multimedia Systems Selector.


ta,
Nolander

---

### Post by atomkarinca on 2007-08-02
system > preferences > sound > devices tab

i guess you can play with this and see the results.

---

### Post by Nolander on 2007-08-02
i tried all the options and when i hit test it tell me
```
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=music: Could not open resource for writing
```

ta,
Nolander.

---

### Post by atomkarinca on 2007-08-02
it could be esd problem. type this in terminal:

sudo killall esd

does it work now?

---

### Post by Nolander on 2007-08-02
```
sudo killall esd
```

could my sound driver not be installed. if so how do i install it?

ta, 
Nolander

---

### Post by atomkarinca on 2007-08-02
type lspci in the terminal give us the output.

---

### Post by Nolander on 2007-08-02
```
00:00.0 Host bridge: VIA Technologies, Inc. P4M266 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP]
00:11.0 ISA bridge: VIA Technologies, Inc. VT8233 PCI to ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1b)
00:11.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1b)
00:11.4 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1b)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 70)
01:00.0 VGA compatible controller: S3 Inc. VT8375 [ProSavage8 KM266/KL266]

```

and thank for helping me.

---

### Post by atomkarinca on 2007-08-02
do you have alsa installed? if not, install it using:

sudo apt-get install alsa-base alsa-utils

and try again.

---

### Post by Nolander on 2007-08-03
there already installed.

---

### Post by MadTxn on 2007-08-05
i'm having the same problem.  After a little troubleshooting, I *believe* it's something with firefox.  Try closing Totem, closing firefox, then open totem again.  If you are like me, the sound will work.  I'm not sure what's going on.

---


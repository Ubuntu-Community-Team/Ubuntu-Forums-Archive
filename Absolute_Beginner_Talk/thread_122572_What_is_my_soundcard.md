---
title: "What is my soundcard?"
date: 2006-01-28
forum: Absolute Beginner Talk
---

### Post by SilverTab on 2006-01-28
I tried;

lspci

and I got the following:

```

0000:00:00.0 Host bridge: Intel Corp.: Unknown device 2770 (rev 81)
0000:00:01.0 PCI bridge: Intel Corp.: Unknown device 2771 (rev 81)
0000:00:1b.0 0403: Intel Corp.: Unknown device 27d8 (rev 01)
0000:00:1d.0 USB Controller: Intel Corp.: Unknown device 27c8 (rev 01)
0000:00:1d.1 USB Controller: Intel Corp.: Unknown device 27c9 (rev 01)
0000:00:1d.2 USB Controller: Intel Corp.: Unknown device 27ca (rev 01)
0000:00:1d.3 USB Controller: Intel Corp.: Unknown device 27cb (rev 01)
0000:00:1d.7 USB Controller: Intel Corp.: Unknown device 27cc (rev 01)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev e1)
0000:00:1f.0 ISA bridge: Intel Corp.: Unknown device 27b8 (rev 01)
0000:00:1f.1 IDE interface: Intel Corp.: Unknown device 27df (rev 01)
0000:00:1f.2 IDE interface: Intel Corp.: Unknown device 27c0 (rev 01)
0000:00:1f.3 SMBus: Intel Corp.: Unknown device 27da (rev 01)
0000:01:00.0 VGA compatible controller: nVidia Corporation: Unknown device 0161 (rev a1)
0000:02:00.0 Communication controller: Lucent Microelectronics V.92 56K WinModem (rev 03)
0000:02:03.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
0000:02:08.0 Ethernet controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) LAN Controller (rev 01)

```


Can't figure out what my soundcard is in there???

Sound works, but I can't have more than 2 sounds at once (ex: I cant open xmms if totem is already opened etc...)
so I tried to follow a guide...to fix that...problem is, I cant locate my soundcard...no idea what the model is...(if I remember well in windows it said C-Panel audio card or something like that)

---

### Post by heimo on 2006-01-28
I'm probably not going to be able to help you - but let's try anyway. :) Is your computer some big brand box? Do you know the exact model? (May be written on a label on your computer.) Do you know if you're using sound card or integrated audio chip on the motherboard? (Is the audio cables coming from an extension slot, or are the connectors near other connectors like keyboard/mouse/usb...) This may give us some hints of what's your audio card.

Personally I seem to have a file /proc/asound/cards with this content:
```
0 [V8237          ]: VIA8237 - VIA 8237
                     VIA 8237 with ALC655 at 0xeb00, irq 22

```
And I know that my sound is integrated to via chipset (south bridge) 8237. Try running this in terminal window:
```
cat /proc/asound/cards

```

---

### Post by Puptentacle on 2006-01-28
I don't see anything that looks like a soundcard in the list you posted, and nothing rings a bell about c-panel. 

You might have to go "low tech", open the case and take a look at the soundcard.

---

### Post by SilverTab on 2006-01-28
```

cat /proc/asound/cards
0 [Intel          ]: HDA-Intel - HDA Intel
                     HDA Intel at 0xfdff8000 irq 16

```

---

### Post by SilverTab on 2006-01-28
this is of any help ?? does it mean my card is an intel one?

---

### Post by heimo on 2006-01-28
Yeah. It's one of those Intel "high definition audio" chips and I've seen some threads discussing problems with Intel HDA audio, but could be that it was with version 5.04 - as this wiki page suggests:
[https://wiki.ubuntu.com/HdaIntelSoundHowto](https://wiki.ubuntu.com/HdaIntelSoundHowto)

Are you using "Breezy Badger", Ubuntu version 5.10? You should probably search the forums, should be easier now when you know the audio chip (intel hda). Sorry, I can't help more on this subject. But if it helps, I'd probably go to System->Preferences->Multimedia Systems Selector and play with settings there.

---

### Post by Galoot on 2006-01-28
You could also try [FONT="Courier New"]sudo lshw | less[/FONT] and scroll down to the multimedia section to find out if there's more info about your sound.

---


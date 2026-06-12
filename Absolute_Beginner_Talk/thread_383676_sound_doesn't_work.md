---
title: "sound doesn't work"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by gildelcour on 2007-03-13
Hi

I'm totally new to ubuntu and linux but so far i like it. I've installed ubuntu now (dual boot w windows, some problems with ati graphics) but I don't get any sound at all, not with amarok, not with youtubevideos, no startupsounds,... I've checked that PCM = 100%

Any help would be great
tnx

Gil

---

### Post by TwoWordz on 2007-03-13
Hi,

Are you using headphones or speakers? Did you plug them in the front jack?

Please type lspci in a console and send the result here. 

TW

---

### Post by gildelcour on 2007-03-14
Thanx mate, I'm using speakers (Dell) that work ok in win xp

output for lspci:

0000:00:00.0 Host bridge: Intel Corporation 945G/P Memory Controller Hub
0000:00:01.0 PCI bridge: Intel Corporation 945G/P PCI Express Graphics Port
0000:00:1b.0 0403: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
0000:00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
0000:00:1c.4 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 5 (rev 01)
0000:00:1c.5 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 6 (rev 01)
0000:00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
0000:00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
0000:00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
0000:00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)
0000:00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
0000:00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
0000:00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
0000:00:1f.2 0106: Intel Corporation 82801GR/GH (ICH7 Family) Serial ATA Storage Controllers cc=AHCI (rev 01)
0000:00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc RV370 5B62 [Radeon X600 (PCIE)]
0000:01:00.1 Display controller: ATI Technologies Inc Radeon X600(RV380)
0000:05:08.0 Ethernet controller: Intel Corporation 82801G (ICH7 Family) LAN Controller (rev 01)

Gil

---

### Post by TwoWordz on 2007-03-14
Hello, 

Here you can see the controller used by your system:

```
0000:00:1b.0 0403: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
```

There is a lot of documentation on the forums about this particular controller. 

You can try to set your BIOS sound card settings to AC'97 instead of HDA, it can help. 

Also, use alsamixer (type it in a console) to push all outputs to the maximum. 

You can use aplay (in a console) to see if the subsystem works:

```
aplay /usr/share/sounds/gnometris/turn.wav
```

if it doesn't try it with sudo to see if it is a right problem:

```
sudo aplay /usr/share/sounds/gnometris/turn.wav
```

TW

---

### Post by gildelcour on 2007-03-14
Well, 
I allready tried the alsamixer, nothing is muted
The wav files wont play (not with and not without the sudo command)
And how do I change the BIOS settings?
I tried System/preferences/sound, but HDA is the only option I have at the bottom

---

### Post by TwoWordz on 2007-03-14
To change the bios settings, when the computer boots, push DELETE, on some computers it is F2. 

Inside the bios, look for integrated peripherals, you should see the audio mode for your device. 

TW

---

### Post by mendingo84 on 2007-03-14
have you installed libxine-extracodecs package?
> 
sudo apt-get install libxine-extracodecs

---

### Post by gildelcour on 2007-03-14
I allready have the updated version of libxine-extracodecs package
I tried the F2 button when booting (Delete didnt work), but all I could do was change enable/disable the integrated audio something, it was enabled, I tried to disable it, but now I can't even use my volumecontrol anymore so I guess I'll enable that again...

Gil

---


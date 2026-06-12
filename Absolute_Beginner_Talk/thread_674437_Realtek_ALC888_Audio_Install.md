---
title: "Realtek ALC888 Audio Install"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by Cal55 on 2008-01-21
Has anyone got the Realtek ALC888 Audio working in Ubuntu Gutsy 7.10 ?

This was not detected/setup by my install.  

```
aplay -l
```
gives :-
```
aplay: device_list : 204: no soundcards found
```

I have tried downoading the driver from realtek.co.tw, unpacking it and then doing 
```
sudo ./install
```

A subsequent re-boot left me unable to log-in.  I have thus had to re-install.

Does anyone know an approved way to get the ALC888 working in Gutsy?  Preferably without too much risk to the existing install?  

Much of the help on soundcards seems pre-7.10, so it's difficult for me to know what's dangerous.

Help much appreciated.

Chris

---

### Post by Cal55 on 2008-01-22
Anybody able to help on this.

I followed the instructions on the HdaIntelSoundHowTo :-
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

And altered to cater for an alsa driver downloaded from Realtek.co.tw:-
[http://ubuntuforums.org/showthread.php?t=550753&page=11](http://ubuntuforums.org/showthread.php?t=550753&page=11)

But still no joy.
```
cat /proc/asound/card0/codec#* | grep Codec
```
gives : cat: /proc/asound/card0/codec#*: No such file or directory

Incidentally no /asound/ exists under /proc/ 

Any thoughts?

Cheers
Chris

---

### Post by BobCFC on 2008-01-22
I have an MSI P35 Platinum which says on the website:  Chip integrated by Realtek® ALC888/ALC888T


Audio works out of the box on gutsy..  when I did the aplay -l command it said I was using an earlier driver:

card 0: Intel [HDA Intel], device 1: ALC883 Digital [ALC883 Digital]


Even though the codec command shows later:

Codec: Realtek ALC888


Audio is not a problem I've had to fix on Ubuntu but If you want me to run any commands just ask.  On PCLinux OS I had to download the latest alsa from the website but ubuntu has never caused problems.

---

### Post by Cal55 on 2008-01-22
Many thanks for the response BobCFC.  It's helpful to know that someone has a working sound driver with a similar mobo.  Makes me think BIOS settings, but that could be way out.

I'm generally a bit bemused as to whether it's a Realtek chip or an Nvidia one.  The mobo manual suggests  Realtek but lspci suggests Nvidia.

I need to do  a bit of other work first, but would like to come back to you with a couple of questions re your config if that's ok?  Probably tomorrow 23/01. 

Cheers
Chris

---

### Post by Cal55 on 2008-01-23
Hi BobCFC.

Would it be possible to let me have a listing of the results of 'lspci' on your machine.  

I'm starting to worry that this is something more fundamental than just sound.  I see that I have lots of unknown devices listed in lspci :-

[http://ubuntuforums.org/showthread.php?t=676032](http://ubuntuforums.org/showthread.php?t=676032)

Also, do you know what chipset your mainboard has?  Mine's apparently an nVidia MCP73U/PV/U which I'm starting to think might be new/not supported.

cheers
Chris

---

### Post by BobCFC on 2008-01-24
```
gg64@conroe:~$ lspci
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G80 [GeForce 8800 GTS] (rev a2)
03:00.0 IDE interface: Marvell Technology Group Ltd. 88SE6121 SATA II Controller (rev b1)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
05:02.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev c0)
```

Hope this helps,

 I'm not sure which chipset you mean?  I don't have on-board graphics just an MSI P35 Platinum that came out in the summer... you can see the details [here]("http://global.msi.com.tw/index.php?func=proddesc&prod_no=1212&maincat_no=1")

---

### Post by Cal55 on 2008-01-24
Thanks BobCFC.  Yes, your board has an Intel® P35 Chipset.  Mine is Nvidia NFORCE-MCP73 (that's the actual chipset of the board, not the onboard graphics...which is of course also Nvidia).  It's the chipset that's giving me the problems.  Most of my PCI devices are thus not recognised :- 

```
00:00.0 Host bridge: nVidia Corporation Unknown device 07c1 (rev a2)
00:00.1 RAM memory: nVidia Corporation Unknown device 07cb (rev a2)
00:01.0 RAM memory: nVidia Corporation Unknown device 07cd (rev a1)
00:01.1 RAM memory: nVidia Corporation Unknown device 07ce (rev a1)
00:01.2 RAM memory: nVidia Corporation Unknown device 07cf (rev a1)
00:01.3 RAM memory: nVidia Corporation Unknown device 07d0 (rev a1)
00:01.4 RAM memory: nVidia Corporation Unknown device 07d1 (rev a1)
00:01.5 RAM memory: nVidia Corporation Unknown device 07d2 (rev a1)
00:01.6 RAM memory: nVidia Corporation Unknown device 07d3 (rev a1)
00:02.0 RAM memory: nVidia Corporation Unknown device 07d6 (rev a1)
00:03.0 ISA bridge: nVidia Corporation Unknown device 07d7 (rev a2)
00:03.1 SMBus: nVidia Corporation Unknown device 07d8 (rev a1)
00:03.2 RAM memory: nVidia Corporation Unknown device 07d9 (rev a1)
00:03.3 Co-processor: nVidia Corporation Unknown device 07da (rev a2)
00:03.4 RAM memory: nVidia Corporation Unknown device 07c8 (rev a1)
00:04.0 USB Controller: nVidia Corporation Unknown device 07fe (rev a1)
00:04.1 USB Controller: nVidia Corporation Unknown device 056a (rev a1)
00:08.0 IDE interface: nVidia Corporation Unknown device 056c (rev a1)
00:09.0 Audio device: nVidia Corporation Unknown device 07fc (rev a1)
00:0a.0 PCI bridge: nVidia Corporation Unknown device 056d (rev a1)
00:0b.0 PCI bridge: nVidia Corporation Unknown device 056e (rev a1)
00:0c.0 PCI bridge: nVidia Corporation Unknown device 056f (rev a1)
00:0d.0 PCI bridge: nVidia Corporation Unknown device 056f (rev a1)
00:0e.0 IDE interface: nVidia Corporation Unknown device 07f0 (rev a2)
00:0f.0 Ethernet controller: nVidia Corporation Unknown device 07dc (rev a2)
02:00.0 VGA compatible controller: nVidia Corporation GeForce 8600 GT (rev a1)
```

So I think I'm scuppered for now, until the Linux kernel supports my chipset.  Perhaps I should eBay this mainboard to a Windozer...and buy one like yours!!:sad:

Thanks for the help.

Chris

---

### Post by anemptygun on 2008-02-16
BobCFC does the Realtek ALC888 have input support?

---

### Post by BobCFC on 2008-02-17
I certainly have Line In / Mic In controls on my mixer applet... it even has extra mic in/headphones sliders for the ports on the front of my case that I connected.

But the truth is the *inputs* haven't been used -  I don't think I even have a microphone anymore lol. 

If I can find some device to test the sockets I will.

---

### Post by binsiram on 2008-03-13
I am also in the same boat as Cal...
the output for lscpi shows 

lspci
00:00.0 Host bridge: nVidia Corporation Unknown device 07c0 (rev a2)
00:00.1 RAM memory: nVidia Corporation Unknown device 07cb (rev a2)
00:01.0 RAM memory: nVidia Corporation Unknown device 07cd (rev a1)
00:01.1 RAM memory: nVidia Corporation Unknown device 07ce (rev a1)
00:01.2 RAM memory: nVidia Corporation Unknown device 07cf (rev a1)
00:01.3 RAM memory: nVidia Corporation Unknown device 07d0 (rev a1)
00:01.4 RAM memory: nVidia Corporation Unknown device 07d1 (rev a1)
00:01.5 RAM memory: nVidia Corporation Unknown device 07d2 (rev a1)
00:01.6 RAM memory: nVidia Corporation Unknown device 07d3 (rev a1)
00:02.0 RAM memory: nVidia Corporation Unknown device 07d6 (rev a1)
00:03.0 ISA bridge: nVidia Corporation Unknown device 07d7 (rev a2)
00:03.1 SMBus: nVidia Corporation Unknown device 07d8 (rev a1)
00:03.2 RAM memory: nVidia Corporation Unknown device 07d9 (rev a1)
00:03.3 Co-processor: nVidia Corporation Unknown device 07da (rev a2)
00:03.4 RAM memory: nVidia Corporation Unknown device 07c8 (rev a1)
00:04.0 USB Controller: nVidia Corporation Unknown device 07fe (rev a1)
00:04.1 USB Controller: nVidia Corporation Unknown device 056a (rev a1)
00:08.0 IDE interface: nVidia Corporation Unknown device 056c (rev a1)
00:09.0 Audio device: nVidia Corporation Unknown device 07fc (rev a1)
00:0a.0 PCI bridge: nVidia Corporation Unknown device 056d (rev a1)
00:0b.0 PCI bridge: nVidia Corporation Unknown device 056e (rev a1)
00:0c.0 PCI bridge: nVidia Corporation Unknown device 056f (rev a1)
00:0d.0 PCI bridge: nVidia Corporation Unknown device 056f (rev a1)
00:0e.0 IDE interface: nVidia Corporation Unknown device 07f0 (rev a2)
00:0f.0 Ethernet controller: nVidia Corporation Unknown device 07dc (rev a2)
00:10.0 VGA compatible controller: nVidia Corporation Unknown device 07e0 (rev a2)
04:00.0 FireWire (IEEE 1394): JMicron Technologies, Inc. Unknown device 2380


does that mean that ubuntu does not support realtek card :(

---

### Post by rickyrockrat on 2008-03-26
The ALC888 is not the issue. The issue is getting the Nvidia chipset to talk to the ALC888. I have pretty much full support on the ALC888 w/ ICH9.

---


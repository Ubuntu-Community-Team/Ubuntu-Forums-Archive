---
title: "sound driver"
date: 2005-09-17
forum: Absolute Beginner Talk
---

### Post by tray02 on 2005-09-17
I'm not sure what I am supposed to do to fix my sound...I have this crappy emachine and it didn't come with a sound card...the sound is "on board" I guess...but I don't know what to do....if I have to get a driver...I'm not sure which one....What am I looking for? (what might be a problem was that it was originally supposed to run windows xp home edition....)

thank you for your help.

---

### Post by GTvulse on 2005-09-17
[QUOTE=tray02]I'm not sure what I am supposed to do to fix my sound...I have this crappy emachine and it didn't come with a sound card...the sound is "on board" I guess...but I don't know what to do....if I have to get a driver...I'm not sure which one....What am I looking for? (what might be a problem was that it was originally supposed to run windows xp home edition....)

thank you for your help.[/QUOTE]
 Hi tray02. Start by telling us the motherboard model, or at least the vendor's model (if it is a canned computer, say from Gateway or Dell...).

---

### Post by tray02 on 2005-09-17
Full specs for eMachines T2341
Processor
Clock speed 	1.9 GHz

Processor type 	Athlon XP

Installed processor qty 	1

Max supported processor qty 	1

Processor manufacturer 	AMD

Processor performance index 	2400+
RAM
RAM installed 	128 MB

Memory specification compliance 	DDR266/PC2100

Memory speed 	266 MHz

RAM form factor 	DIMM 184-pin

RAM technology 	DDR SDRAM
Video Output
Graphics processor 	VIA ProSavageDDR KM266

Graphics card name 	Integrated S3 ProSavage8

Video output form factor 	Integrated

Video output type 	Graphics adapter
Display (Projector)
Display type 	None.
Service & Support
Service & Support type 	1 year warranty
Optical Storage
CD / DVD type 	CD-RW

CD / DVD read speed 	48x

CD / DVD rewrite speed 	24x

CD / DVD write speed 	48x

Optical storage interface type 	IDE
Storage Hard Drive
Hard drive interface 	IDE/ATA

Hard drive installed qty 	1

Hard drive size 	40 GB

Hard drive type 	Standard
Interface Provided
Interface 	6 Hi-Speed USB, 1 Serial RS-232, 1 Parallel IEEE 1284 (EPP/ECP), 1 Keyboard Generic, 1 Mouse Generic, 1 Modem Phone line, 1 Network Ethernet 10Base-T/100Base-TX, 1 Display / video VGA, 2 Microphone Input, 1 Headphones Output, 1 Audio Line-in, 1 Audio Line-out

Connector Type 	4 pin USB Type A, 9 pin D-Sub (DB-9), 25 pin D-Sub (DB-25), 6 pin mini-DIN (PS/2 style), 6 pin mini-DIN (PS/2 style), RJ-11, RJ-45, 15 pin HD D-Sub (HD-15), Mini-phone 3.5 mm, Mini-phone stereo 3.5 mm, Mini-phone stereo 3.5 mm, Mini-phone stereo 3.5 mm
Storage Hard Drive (2nd)
2nd hard drive type 	None
Optical Storage (2nd)
2nd optical storage type 	None
Storage Controller (2nd)
2nd storage controller type 	None
Modem
Modem 	56 Kbps Fax / modem PCI Plug-in card

Modem protocols & specifications 	ITU V.92
Audio Output
Audio output form factor 	Integrated

Audio output type 	Sound card
Cabinet (Chassis)
Cabinet form factor 	Tower
Cache Memory
Cache 	256 KB L2 cache

Cache per processor size 	256 KB
Mainboard
Chipset type 	VIA ProSavageDDR KM266

Data bus speed 	266 MHz
Cluster
Storage 	None HD

Storage Controller 	None
Networking
Data link protocol 	Ethernet, Fast Ethernet

Networking 	Network adapter Integrated
Dimensions & Weight
Depth 	16 in

Height 	14.1 in

Width 	7.2 in
Bay Provided
Expansion bays 	2 (1 free) Front accessible 5.25" x 1/2H, 1 (0 free) Front accessible 3.5" x 1/3H, Internal 3.5" x 1/3H
Storage Floppy Drive
Floppy drive type 	3.5" 1.44 MB floppy
Service & Support Details
Full contract period 	1 year, 1 year

Service & Support details 	Limited warranty, Technical support

Service included 	Parts and labor, Phone consulting
Input Device
Input device 	Mouse, Keyboard
Power Device
Power device type 	Power supply
Video Memory
Video memory technology 	Shared video memory (UMA)
System
Recommended use 	Home use

System type 	Personal computer
OS Provided
OS provided 	Microsoft Windows XP Home Edition
Storage Removable
Removable storage type 	None
Slot Provided
Slot provided 	1 (0 free) Processor Socket A, Memory DIMM 184-pin, 1 (1 free) AGP 4x, 3 (2 free) PCI
Storage Controller
Storage controller form factor 	Integrated

Storage controller installed qty 	1

Storage controller interface type 	IDE/ATA

Storage controller type 	IDE
Software
Software type 	Microsoft Works 6.0, Microsoft Money 2002



....that enough info for ya...


....alright...Fullmetal....

---

### Post by GTvulse on 2005-09-17
OK. According to [http://forum.linspire.com/viewtopic.php?t=410883&sid=40b7a6c901826fa6e5918243e3c9fd95](http://forum.linspire.com/viewtopic.php?t=410883&sid=40b7a6c901826fa6e5918243e3c9fd95), your mainboard has a VIA 82C686A/B rev 50 chipset in the South Bridge. When you type "lsmod" at a terminal, does the output contain an entry of the form snd_via82cxxx?

If that is the case, you may have the sound muted (and that would show in the sound control in the upper right corner of the gnome desktop as a little x, that can be hard to see sometimes). If that is the case, type "alsamixer" at a terminal and make sure that the master volume control is active. Then type "sudo alsactl store" to make sure the setting file is written to disk and you should have sound then.

On hagarennorekinjutsushin.... Hughes and I look like twin brothers and I'm handy with knives too...  :-P

---

### Post by tray02 on 2005-09-17
I'm pretty sure that it is NOT muted....

---

### Post by GTvulse on 2005-09-17
[QUOTE=tray02]I'm pretty sure that it is NOT muted....[/QUOTE]
And did you check the kernel module is loading?

---

### Post by tray02 on 2005-09-18
in idiot's terms that would mean....


...how do I do that...

---

### Post by GTvulse on 2005-09-18
[QUOTE=tray02]in idiot's terms that would mean....
[/quote]
I take it you mean layman, or newbie...  :-P
>  
...how do I do that...
That would be the output of lsmod. If you type ```
lsmod | grep via
```, you should see a listing and among the lines there should be several similar to these:
```

snd_via82xx            25792  1
gameport               14472  2 analog,snd_via82xx
snd_ac97_codec         71804  1 snd_via82xx
snd_pcm                78344  3 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         10120  2 snd_via82xx,snd_pcm
snd_mpu401_uart         6784  1 snd_via82xx
snd                    48644  13 snd_seq_oss,snd_seq,snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device

```
If that is not the case, you can try loading the modules by hand:
```

-$ sudo modprobe snd_via82xx snd_ac97_codec snd_pcm snd_pcm_oss snd_page_alloc snd_mpu401_uart snd snd_seq_oss 

```
Those are not all the modules that may be required but you get the idea.

If inserting the sound modules into the running kernel gives you working sound, the problem is that the start up detection scripts are failing for some reason. In that case you could edit the start-up module loading config file:
```
-$ sudo gedit /etc/modules.conf
``` add snd_via82xx to the list and reboot; read the manual pages for modprobe and modeprobe.conf first:
```
-$ man modprobe 
-$ man modprobe.conf
```

You can learn about kernel module loading in the [Linux Loadable Kernel Module HOWTO](http://www.tldp.org/HOWTO/Module-HOWTO/). 

If this doesn't work, the problem is probably that the kernel has trouble supporting your particular combination of hardware. If you are using Hoary (Ubuntu 5.04), you may try upgrading to Breezy (Ubuntu 5.10). You don't need to delete your present installation, but rather do a dist-upgrade. I won't explain it to you here, rather do a quick search in the forums and you'll find more threads with instructions on how to do it than you can shake a stick at.

Good luck!

---

### Post by tray02 on 2005-09-18
does this HOWTO guide have a printable version...or is there a book I can buy....?/??

---

### Post by GTvulse on 2005-09-18
[QUOTE=tray02]does this HOWTO guide have a printable version...or is there a book I can buy....?/??[/QUOTE]
Go to the home page of [The Linux Documentation Project](http://www.tldp.org/) and start from there. Most documents in tldp.org are available as downlodable html bundles and pdf as well.

---


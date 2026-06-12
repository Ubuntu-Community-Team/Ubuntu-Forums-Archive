---
title: "[SOLVED] no sound in kubuntu..."
date: 2007-12-07
forum: Absolute Beginner Talk
---

### Post by staticvoid on 2007-12-07
...and I'm sad :(

I have a sony vaio pcg-tr3a with an intel sound card. If you need more specs, tell me how I can get them in the terminal.

Thanks a bunch for your help :)


sv

---

### Post by forestpixie on 2007-12-07
not sure I'm going to be able to help here but to start with can you do this

lspci 

and can we assume that you've not got any muted channels, also don't know if you have a digital/analogue switch if you have is it set right 

and also - 

has it stopped working, or has it never worked , did you have feisty and it worked then, upgraded and it's stopped - or have you just installed and it just doesn't work

---

### Post by khurrum1990 on 2007-12-07
Hi, first of all type "alsamixer" in the konsole and make sure nothing is on mute and volume is full up. If this doesn't help them post the output of:
1. lspci
2. dmesg
You can do this in konsole.
It could be possible u need the latest alsa drivers. Download their source code from their website, just search for them in google if u want. Then u need to compile and install them.
Make sure u have ur build essentials, u can install them by typing in konsole:
sudo apt-get install build-essentials

Try this and tell us what happened.

---

### Post by staticvoid on 2007-12-07
1.** lspi**
```
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
02:05.0 CardBus bridge: Ricoh Co Ltd RL5c475 (rev b8)
02:05.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C551 IEEE 1394 Controller
02:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller (rev 83)
02:0b.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)

```
2. **dmesg**
```
[   63.844000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   63.844000] apm: overridden by ACPI.
[   64.284000] sonypi: Sony Programmable I/O Controller Driver v1.26.
[   64.288000] sonypi: please try the sony-laptop module instead and report fail
ures, see also http://www.linux.it/~malattia/wiki/index.php/Sony_drivers
[   64.292000] sonypi: detected type2 model, verbose = 0, fnkeyinit = off, camer
a = off, compat = off, mask = 0xffffffff, useinput = on, acpi = on
[   64.292000] sonypi: enabled at irq=11, port1=0x1080, port2=0x1084
[   64.292000] sonypi: device allocated minor is 63
[   64.352000] input: Sony Vaio Jogdial as /class/input/input7
[   64.380000] input: Sony Vaio Keys as /class/input/input8
[   64.932000] sony-laptop: Sony Notebook Control Driver v0.5.
[   64.960000] input: Sony Vaio Keys as /class/input/input9
[   64.976000] input: Sony Vaio Jogdial as /class/input/input10
[   66.164000] [drm] Initialized drm 1.1.0 20060810

```

sorry... what section of this information did you want? Its a lot... with like my IP addy er MAC address... uh. :-/

In ubuntu 7.10 I had to do this wierd thing: crank up the volume, set all the controllers to control psm (whatever its called) and then activate the external amplifier and then uncheck it.

yes, it was a very strange procedure... So you say I should check out some more recent alsa drivers?

oh and if you want the last output for the command, just ask agin :) sorry...

sv

---

### Post by forestpixie on 2007-12-07
I've had a bit of a dig around for the Intel Corporation 82801DB/DBL/DBM and there seem to be some problems 

found one where the op had needed to switch off external amplifier which ties up with your post

this was the search [results]("http://www.uboontu.com/results.htm?cx=002072379199720138921%3A9m-bgfzutzq&cof=FORID%3A10&q=intel+82801db+no+audio&sa.x=61&sa.y=24&sa=Search#1296")


sorry can't be of more help other than to say make sure you have got all relevant controls set right

---

### Post by staticvoid on 2007-12-07
woah :) thats a cool search site.

thanks for your help.

I'll keep hoping that someone shows up with a sony vaio tr3a with kubuntu and fixed sound problem :) heheh...

I'll check out those search results and post something if I can get it fixed. Its deffinatly a wierd issue. I mean c'mon, external amplifier turned on and unchecked? what does that do?? haha..


sv

---

### Post by staticvoid on 2007-12-07
WWOOOOHHOOO!!!!!!

:)

```
sudo alsamixer

```
arrow key right > > > > > > until you get to "External" and hit 
```
m

```
then hit "esc"

then open up amarok and listen to the guys funny accent :D

so yeah, i'm happy. hope this helps some one else.

external + intel = eeeeeviiil

ciao amigos!
viva la musica!

static void

---

### Post by staticvoid on 2007-12-07
or.. just go to the menu for the sound and unswitch external with the.. yellow button? haha... a little hard to figure out

---

### Post by forestpixie on 2007-12-07
excellent glad I could help in a roundabout way - 

> woah  thats a cool search site.
 I thought so put it in my search engine thingummy :)

---

### Post by staticvoid on 2007-12-08
hehe.. me too :)

ubooooooooooontu

---

### Post by Mr Potter on 2008-02-12
You guys rock! Thanks so much for figuring this out!

---


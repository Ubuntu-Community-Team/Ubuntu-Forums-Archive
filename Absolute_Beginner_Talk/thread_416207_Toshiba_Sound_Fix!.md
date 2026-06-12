---
title: "Toshiba Sound Fix!"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by bobtherocket on 2007-04-20
Ok, lots of threads about the Toshiba sound not working well with Feisty...I found a fix...May be a bit sloppy, but I'm a newb.

EDIT: This works with the ALC861 and Intel HDA sound drivers, just to specify...I know it's not just for Toshiba.

Open terminal.

```

cd /etc/init.d

```

Create a new text file:

```

sudo gedit soundstartfix

```

Text to stick in:

```

#!/bin/bash
kill $(lsof -t /dev/dsp* /dev/audio* /dev/mixer* /dev/snd/*)
sudo modprobe -r snd-hda-intel && sudo modprobe snd-hda-intel model=auto

```
Save, then close the text editor.

Now you need to make it start with other schtuff, soo...
```

sudo update-rc.d soundstartfix defaults

(Wait for it to finish, then:)

sudo chmod +x soundstartfix

```

Reboot, and it should be working perfectly!

---

### Post by jiminycricket on 2007-04-20
Hi,
perhaps this can be in the Howto forum too, for archiving.

Thanks for posting this.

---

### Post by dangerpl on 2007-04-21
Perfect :) That resolves my problem with sound :) Make sure to spread this! There's quite a few people dealing with this problem!

---

### Post by greenie9 on 2007-04-21
its cause me worse problems than i previously had...

before sound was always on, and at its loudest, no matter what (mute-ing sound, turning it down did nothing), i applied this and now i get the error message

>  No volume control GStreamer plugins and/or devices found 

can you please tell me either how to undo do this, or how to fix current problem...

btw i have an asus f3j laptop with a audio Intel 82801G (ICH7 Family) (rev 02) sound card if that matters at all...

---

### Post by bobtherocket on 2007-04-21
This fix is specifically for the Intel HDA drivers...

---

### Post by greenie9 on 2007-04-21
> **bobtherocket said:**
> This fix is specifically for the Intel HDA drivers...

it is a HDA driver

[QUOTE=result of lspci]00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce Go 7600] (rev a1)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
06:01.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832
06:01.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
06:01.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)
06:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
[/QUOTE]

ive deleted the contents of the soundstart fix file, so my sound is back to being full volume... and whilst i can move the volume bar up and down, this has no affect on sound levels... 

its rather annoying, so any/all help on this would be appreciated

---

### Post by LuCiAn0 on 2007-04-21
Not worked:confused:  here, everything works great but NO SOUND :confused:

---

### Post by psyke83 on 2007-04-21
Hi,

A less hacky way to do the same is to edit /etc/modprobe.d/alsa-base and add to the end of the file:

```
options snd-hda-intel model=auto
```

Changes will take effect after a reboot.

---

### Post by granite230 on 2007-04-21
> **psyke83 said:**
> Hi,

A less hacky way to do the same is to edit /etc/modprobe.d/alsa-base and add to the end of the file:

```
options snd-hda-intel model=auto
```

Changes will take effect after a reboot.

What a relief! It works! Thanks for your solution! :-D

---

### Post by greenie9 on 2007-04-21
didnt work for me :(

---

### Post by ben_jammin on 2007-04-21
i'm on a toshiba p100 473, and none of these fixes worked ...

---

### Post by peter07 on 2007-04-22
No sound after update - it didnt work for me :(

---

### Post by rax_m on 2007-04-22
For some Toshiba laptops, the ACPI is an issue. The following post talks about how to resolve. 

[http://ubuntuforums.org/showthread.php?t=349491&highlight=toshiba+p100-429](http://ubuntuforums.org/showthread.php?t=349491&highlight=toshiba+p100-429)

In some cases, the newer version of Alsa drivers are also required

---

### Post by fastb on 2007-04-22
Can someone please help me. 
My sound was really low and I tried to fix that by compiling new alsa drivers. It didn't work because there were some errors while compiling. And now when I try to test the sound in the sound section under preferences that program crashes. And now none of your solutions work. Does anyone know how can I undo my actions and put the things like they were when I fresh installed ubuntu. I want to just install the old drivers. I tried in synaptic to reinstall alsa drivers but it doesn't work.

Thanks

---

### Post by lazyrussian on 2007-04-23
Does anyone know if this will wokr for a A105-s2101 laptop? I dont have the ALC chipset, just some integrated 3D sound chipset - atleast that's what tigerdirect tells me.

I'm a bit hesitant to upgrade if this fix doesn't work...I had to downgrade over the weekend.

---

### Post by lazyrussian on 2007-04-23
Nevermind, I just check again and it seems I have it after all :)

```

arthur@arthur-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC861 Analog [ALC861 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

---

### Post by lazyrussian on 2007-04-23
OK, well my card is definitely aprtially recognized since something is now visible when I type in alsamixer BUT I still have no sound.

Here is the output of aplay -l (the ALC861 is missing)
```

arthur@arthur-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

---

### Post by Uranium235 on 2007-04-23
I'm having the exact same problem with the exact same hardware, LazyRussian.  I just can't seem to get this thing going with sound. :/

---

### Post by lazyrussian on 2007-04-23
I finally got it working.

Here's what you do (I got this from another thread) - Make sure to write these directions down or print them out before you restart - since you'll be doing all of this inside a temrinal system with no real GUI Interface - atleast that's how it worked in kubuntu. The directions are written for both ubuntu and kubuntu. Goodluck!

1. Login into recovery mode (ubuntu) or failsafe mode (kubuntu)
2. When the terminal/konsole pops up enter the following (in this order)

```

sudo rmmod snd-hda-intel
sudo modprobe snd-hda-intel probe_mask=8 model=auto

```

After you do that, login into termina with the 'su' command. Then do the following

```

sudo gedit /etc/modprobe.d/alsa-base

```

When gedit (or kate) opens up, enter the following at the end of the document and save

```

options modprobe snd-hda-intel probe_mask=8 model=auto

```

After you save enter the following command to restart your computer

```

shutdown -r now

```

It should work as soon as you restart.

---

### Post by Uranium235 on 2007-04-23
Ok I'm having some problems getting gedit up in recovery mode.  It keeps giving me the "type gedit --help for a list of options".  Sorry I'm new to this linux thing. :)

edit:

I have sucessfully done all of that now, and I still have no sound. :/

---

### Post by lazyrussian on 2007-04-23
Heh, it's alright :)
But the code below should work.
```

sudo gedit /etc/modprobe.d/alsa-base

```

alsa-base is the file you need to edit. Make sure you enter it exactly as I have written it.

---

### Post by Uranium235 on 2007-04-23
Yeah I've gotten that done and saved, still no sound though.

---

### Post by lazyrussian on 2007-04-23
so the whole process didn't work?

that's crazy. It's worked for everyone with an SB450 card up to this point. 

hmmm, try this method: [http://ubuntuforums.org/showthread.php?t=416207&highlight=toshiba+sound](http://ubuntuforums.org/showthread.php?t=416207&highlight=toshiba+sound)

It didn't work for me but it's worth a shot since it worked for some people with the same card.

Sorry I can't be of any more help. :(

---

### Post by Uranium235 on 2007-04-23
Well now it's not letting me save that soundstartfix file.  It says I don't have permission to do so, and feisty won't let me log in as root from the initial login screen.

---

### Post by Uranium235 on 2007-04-23
Well I have done all of that now and still no sound.  I'm starting to get a bit frustrated

---

### Post by lazyrussian on 2007-04-23
ya that's a bit strange.

Try the soundstrtfix tutorial again except type this in before you 'su'

```

xhost +

```
After that, login as su in terminal and follow the tutorial again.

---

### Post by Uranium235 on 2007-04-23
well that isn't working for me either. :/

---

### Post by lazyrussian on 2007-04-23
I'm sorry - I tried :(

I geuss what you should do is make a new thread in the beginners section (since it is heavily moderated) and post the problem and all the solutions you attempted. See if anyone else gives you any ideas. 

Sorry that I can't be of any more help.

---

### Post by Uranium235 on 2007-04-23
NP man.  I was able to get my ATI drivers going, and that's a start.  Perhaps I'll take a little nap and try tackling it again in an hour or so.  I have a brutal headache now. :)

---

### Post by lazyrussian on 2007-04-23
Heh, best of luck! I had that headache for 5 days (until this morning)

---

### Post by irishScott on 2007-04-23
Might want to change the title too.  Worked for my Acer TM8200 that was having the same problem.

---

### Post by Uranium235 on 2007-04-23
I have tried everything in the book from what I can tell and I've has zero luck.

---

### Post by Lordcoca on 2007-04-24
> **psyke83 said:**
> Hi,

A less hacky way to do the same is to edit /etc/modprobe.d/alsa-base and add to the end of the file:

```
options snd-hda-intel model=auto
```

Changes will take effect after a reboot.

I get an permission denied error when I typed /etc/modprobe.d/alsa-base into the terminal :confused:

---

### Post by greenie9 on 2007-04-24
Lordcoca: you need to use sudo

also, if you run lspci and get the following:

> 00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

try downloading the latest alsa drivers, libs and utils and following the instructions on this web site:

[http://www.w1ldt4ng3nt.net/blog/item/77](http://www.w1ldt4ng3nt.net/blog/item/77)

also, i found that the sound icon was changing CD rather than PCM... 

if "alsamixer" works on your PC try right clicking on the icon, then selecting properties, and make sure that it is changing the PCM track

---

### Post by axle_foley00 on 2007-04-24
> **Lordcoca said:**
> I get an permission denied error when I typed /etc/modprobe.d/alsa-base into the terminal :confused:

You need to use 'sudo' to be able to edit that file. Try this instead:

> sudo gedit /etc/modprobe.d/alsa-base


Hope that helps.

**Edit:** Oops just realised greenie9 suggested this. My bad.

---

### Post by JasonBrunelle on 2007-05-24
I'm planning on buying a Toshiba Satellite® A205-S4577, and want to run linux.  Does anyone know if this model has these sound problems or if they have been fixed with the suggestions on this post (or another post?)

Please let me know.:p

Thanks.

---

### Post by jmeridth on 2007-05-31
Nothing has worked for me, I tried the original script in this post and I've tried adding the options line to the /etc/modprobe.d/alsa-base file with all three options I've seen (auto, 3stack, toshiba).  Nothing has worked.  Please help

I have a Toshiba Satellite P105-S6104

---

### Post by azunino on 2007-05-31
I have no sound with my Toshiba Satellite A205-S4577. I have tried lots of options when 'insmoding' snd-hda-intel with no success (probe_mask=1...8, model=...). I have noticed something strange in dmesg:

...
[ 9065.344000] hda_intel: azx_get_response timeout, switching to polling mode...
[ 9072.156000] ACPI: PCI interrupt for device 0000:00:1b.0 disabled
...

Here is the output of lspci -vvv:

...
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Control: I/O- Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Interrupt: pin A routed to IRQ 21
        Region 0: Memory at f0b40000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=55mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-
        Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
                Address: 0000000000000000  Data: 0000
        Capabilities: [70] Express Unknown type IRQ 0
                Device: Supported: MaxPayload 128 bytes, PhantFunc 0, ExtTag-
                Device: Latency L0s <64ns, L1 <1us
                Device: Errors: Correctable- Non-Fatal- Fatal- Unsupported-
                Device: RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop+
                Device: MaxPayload 128 bytes, MaxReadReq 128 bytes
                Link: Supported Speed unknown, Width x0, ASPM unknown, Port 0
                Link: Latency L0s <64ns, L1 <1us
                Link: ASPM Disabled CommClk- ExtSynch-
                Link: Speed unknown, Width x0
...

Any solution???

thanks

---

### Post by Sparkster185 on 2007-05-31
> **psyke83 said:**
> Hi,

A less hacky way to do the same is to edit /etc/modprobe.d/alsa-base and add to the end of the file:

```
options snd-hda-intel model=auto
```

Changes will take effect after a reboot.

I fixed the sound my my Toshiba by doing this, but instead of "model=auto" I did "model=3stack".

---

### Post by azunino on 2007-05-31
no luck.

[10796.324000] ACPI: PCI interrupt for device 0000:00:1b.0 disabled
[10840.832000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 21
[10840.832000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[10842.152000] si3054: cannot initialize. EXT MID = 0000

Where can I find a list of all the valid model=XXXX values????

---

### Post by AhronZombi on 2007-06-01
Thank you so much. ive been on old kernels for months due to sound. but you got it to work. this is so awsome. KISSSS

---

### Post by ruscoe on 2007-06-01
> **psyke83 said:**
> Hi,
```
options snd-hda-intel model=auto
```

I fixed my Toshiba Satellite with this. Sound works great, but when I plug in my headphones, sound comes out of both the headphones and the laptop speakers simultaneously.

I've tried lots of mucking about with the alsa-mixer to get the speakers to switch off while keeping the headphones switched on, but to no avail. Any ideas?

---

### Post by JasonBrunelle on 2007-06-05
> **JasonBrunelle said:**
> I'm planning on buying a Toshiba Satellite® A205-S4577, and want to run linux.  Does anyone know if this model has these sound problems or if they have been fixed with the suggestions on this post (or another post?)

Please let me know.:p

Thanks.

I bought the laptop, and after over a week's worth of trying various things, have discovered something.  Can anyone else confirm I'm on the right track here?  Or maybe someone knows specifically that I'm not?

Yes, this model has the 82801G HDA Intel Audio controller, and yes, many other models have the same thing, and sound works on them.  This model however, uses the Realtek 268 codec, which has NOT been implemented yet.  I have searched the source code (esp. patch_realtek.c) and it does not list this codec as being supported, and alsa's website doesn't either.  I beleive varying codecs on the HDA controller are why some people are having success with the HDA audio controller and some are not.

cat /proc/asound/cards0 to find out what codec you have.  

I have read something to the effect of an update might be available through a git update for the kernel, but have not tried.  It would likely also be available through an unstable release of ALSA.

I have not yet found that a bug regarding the Realtek 268 codec has been filed with ALSA, so I will do so.  

Lastly, though I wanted to report my findings, I regret that I have switched to Fedora 7 linux, so even if I get it working at this point, I will not be able to give a Ubuntu-specific fix :(.

Thanks for the help!

---

### Post by mcl3130 on 2007-10-21
Hi sorry my bad ingles, only booting acpi=off my sound work. Please help. Toshiba p105-6114. Hda intel,
 Cannot allocate resource region 7 of bridge 0000:00:1c.0
 Cannot allocate resource region 8 of bridge 0000:00:1c.0
 Cannot allocate resource region 9 of bridge 0000:00:1c.0
 Cannot allocate resource region 7 of bridge 0000:00:1c.1
 Cannot allocate resource region 8 of bridge 0000:00:1c.1
 Cannot allocate resource region 9 of bridge 0000:00:1c.1
 Cannot allocate resource region 7 of bridge 0000:00:1c.2
 Cannot allocate resource region 8 of bridge 0000:00:1c.2
 Cannot allocate resource region 8 of bridge 0000:00:1c.2
Thanks.

---

### Post by InsertNameHere on 2007-10-21
Man I love this

3 Days without sound is HELL

---

### Post by vladan.b on 2007-11-06
bobtherocket: Very advanced way to edit the file...but it works!

---

### Post by liv2lrn on 2007-12-06
Hi, I'm new to the whole linux thing. I must say, I was without sound for several days and finally found this post. Thank You, Thank You, Thank You!

---

### Post by LessJohnson on 2007-12-20
thank you, thank you, thank you, thank YOU!

been searching for hours and viola I HAVE SOUND!!!    wwwoooo hooooo

toshiba satellite A105-S361

---

### Post by Waistless on 2008-01-02
It worked!!! Fixed all my problems with the sound being too quiet.

You legend!!! :guitar:

---

### Post by jdgiotta on 2008-03-11
Can anyone verify this works for a Satellite A105 S2141?
I'm running Ubuntu Gutsy Live CD to test my hardware. So far so good; except no sound.

---

### Post by Particleman1701 on 2008-03-17
This fix worked great.  I'm a newbie and really don't understand exactly what this fix does but it fixed my problem 100%.  Thanks for the post!

Toshiba a105-s1014

---

### Post by STG_Fridays on 2008-06-12
bobtherocket

YOU ARE THE MAN!!!

THANKS SO MUCH!!

Three hours of a headache with the sound, trying complicated solutions,but your simple on was the one that actually worked. You F-ing rule.

Btw, I'm running Ubuntu off of a 130 Gig External Hdd on a Toshiba Satellite A135-4727.

---


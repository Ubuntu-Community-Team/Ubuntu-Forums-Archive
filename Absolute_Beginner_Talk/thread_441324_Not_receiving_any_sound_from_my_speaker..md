---
title: "Not receiving any sound from my speaker."
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by rocketboys on 2007-05-12
my sound card is Creative, SBlive 24 bit..

I looked and searched this forum for a longtime, but they are like different sound card and stuff..

Help plz?

p.s 

to use wine, is it correct to go to terminal and type like : wine /cdrom/setup.exe   ?

---

### Post by Acksys on 2007-05-12
What happens if you go to System -> Preferences -> Sound and click one of the test buttons there? If it says "testing," make sure your speakers are connected correctly, volume level is good, etc.

What does running 'lspci' in the terminal say about your card?

---

### Post by rocketboys on 2007-05-12
> **Acksys said:**
> What happens if you go to System -> Preferences -> Sound and click one of the test buttons there? If it says "testing," make sure your speakers are connected correctly, volume level is good, etc.

What does running 'lspci' in the terminal say about your card?

00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 04)
00:01.0 PCI bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL PCI Express Root Port (rev 04)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 05)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 05)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 05)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 05)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 05)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d5)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 05)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 05)
00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 05)
01:0a.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 46)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 19)
04:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7800 GT] (rev a1)

Thank you for the response.

Thats what I got..

and yes, it says it's testing and the volume is good.

but I still can't get any sounds. 

my speaker's power (the led) goes on when I boot the computer, but as soon as I

like few seconds later, it will go off.

---

### Post by the.dark.lord on 2007-05-12
I'm not sure if your driver is restricted or not.

Go to System -> Administration -> Restricted Driver Management

If your sound card is there, enable it.

---

### Post by rocketboys on 2007-05-12
> **the.dark.lord said:**
> I'm not sure if your driver is restricted or not.

Go to System -> Administration -> Restricted Driver Management

If your sound card is there, enable it.

Thank you for the response..

I checked the restricted driver management, but there was only my graphic card's driver...

:'(

---

### Post by FuturePast on 2007-05-12
Type amixer at shell prompt and post results, please.

---

### Post by forestpixie on 2007-05-12
I had similar problem - I had to double click vol icon to get the mixer - changed to switch tab and deselected the digital output jack 

perhaps is a simple as that

---

### Post by rocketboys on 2007-05-12
> **FuturePast said:**
> Type amixer at shell prompt and post results, please.

Thank you for the response

Simple mixer control 'PCM',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB] [on]
  Front Right: Playback 255 [100%] [0.00dB] [on]
Simple mixer control 'Surround',0
  Capabilities: pswitch
  Playback channels: Front Left - Front Right
  Mono:
  Front Left: Playback [off]
  Front Right: Playback [off]
Simple mixer control 'Center',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'LFE',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Side',0
  Capabilities: pswitch
  Playback channels: Front Left - Front Right
  Mono:
  Front Left: Playback [off]
  Front Right: Playback [off]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'PC Speaker',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 15
  Mono:
  Front Left: Playback 15 [100%] [0.00dB] [on]
  Front Right: Playback 15 [100%] [0.00dB] [on]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 30
  Front Left: Capture 0 [0%] [0.00dB] [off]
  Front Right: Capture 0 [0%] [0.00dB] [off]
Simple mixer control 'Capture',1
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 30
  Front Left: Capture 0 [0%] [0.00dB] [off]
  Front Right: Capture 0 [0%] [0.00dB] [off]
Simple mixer control 'Input Source',0
  Capabilities: enum
  Items: 'Front Mic' 'Rear Mic' 'Line' 'CD'
  Item0: 'Front Mic'
Simple mixer control 'Input Source',1
  Capabilities: enum
  Items: 'Front Mic' 'Rear Mic' 'Line' 'CD'
  Item0: 'Front Mic'

I got this..

---

### Post by rocketboys on 2007-05-12
> **forestpixie said:**
> I had similar problem - I had to double click vol icon to get the mixer - changed to switch tab and deselected the digital output jack 

perhaps is a simple as that

Thank you for the respond..I hope mine was like yours, but I guess it isn't...:'(

---

### Post by FuturePast on 2007-05-12
According to your output none of the actual playback channels (Surround, Center, Side, LFE) are on (not muted).
In your Volume Control what sliders do you have for playback?
Try Edit->Preferences to display more.

---

### Post by rocketboys on 2007-05-12
> **FuturePast said:**
> According to your output none of the actual playback channels (Surround, Center, Side, LFE) are on (not muted).
In your Volume Control what sliders do you have for playback?
Try Edit->Preferences to display more.

I have PCM, and PCM Capture.

they both are on max volume...

Thank you for the response!

---

### Post by FuturePast on 2007-05-12
And you clicked Edit-> Preferences in Volume Control?

Alternatively try messing about with $ alsamixer in the terminal.

---

### Post by rocketboys on 2007-05-12
> **FuturePast said:**
> And you clicked Edit-> Preferences in Volume Control?

Alternatively try messing about with $ alsamixer in the terminal.

Thank you for the response!

Yes, I clicked Edit-> Preferences in Volume Control..

and about the alsamixer..I got some other kind of volume control panel. 

And some of the stuff were muted, so unmuted them by pressing "M" button, but 

I I couldn't increase the volume with pressing upper arrow button. ..

---

### Post by FuturePast on 2007-05-12
What happens if you type
$ amixer set Surround 90%

---

### Post by rocketboys on 2007-05-12
> **FuturePast said:**
> What happens if you type
$ amixer set Surround 90%

ugh..

danny@Dan:~$ amixer set Surround 90%
amixer: Invalid command!


:'(

---

### Post by FuturePast on 2007-05-12
I'm sorry, I don't know what else to suggest.

---

### Post by RomeReactor on 2007-05-13
Hi. Sorry to intrude (since I can't really offer any significant advice to help you with your problem); however, I noticed something odd in your lspci output:

> 00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 05)

That looks like an integrated audio card, and the soundblaster doesn't appear to be there. This is what lspci says about my soundblaster:

> 00:08.0 Multimedia audio controller: Creative Labs SB Audigy LS

Perhaps it's not correctly installed? It may help to disable the integrated card in bios, though, again, your SB doesn't seem to be recognized. Did you install the card after installing Ubuntu? If so, maybe installing **ld10k1** and **liblo10k1-0** can help: I remember installing one of them (or both, not sure) when I was running Edgy, and installed my SB Audigy. When Feisty came out, I did a clean install and it configured it correctly (without installing the packages I mentioned). Then again, I still think your Ubuntu hasn't detected your SB card yet; your lspci output just shows the integrated one. Make sure it's correctly inserted in it's pci slot.

---

### Post by oxleyk on 2007-05-13
I recently switched to Feisty to see if Ubuntu is getting better.  Jury's still out.  I've been having what seems to the common problem of no sound.  I have Debian installed on a secondary drive.  I ran alsaconf from Debian and it solved the sound problem.  Maybe the Ubuntu team needs to put alsaconf back in.

Kent

---

### Post by oxleyk on 2007-05-13
> **oxleyk said:**
> I recently switched to Feisty to see if Ubuntu is getting better.  Jury's still out.  I've been having what seems to the common problem of no sound.  I have Debian installed on a secondary drive.  I ran alsaconf from Debian and it solved the sound problem.  Maybe the Ubuntu team needs to put alsaconf back in.

Kent

Just discovered that I have to run alsaconf after every reboot.

---

### Post by hitemhrd on 2007-05-14
I had a setting wrong in the alsamixer and now I have sound. But the quality is poor. Compared to the sounds I got from XP. What can I go to improve the sound quality>

---


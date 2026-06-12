---
title: "GStreamer plugins missing -- the saga continues!"
date: 2007-05-16
forum: Absolute Beginner Talk
---

### Post by whoKnew on 2007-05-16
:(

Hi Everyone.

Tthis is the story so far:

I have recently installed 6.06 (Dapper) on an old ibm thinkpad 600e that I'vei acquired.

I noticed that there is no volume control, and when i try and access the speaker settings, i'm informed that i'm missing some GStreamer plugins. The message: "No volume control GStreamer plugins and/or devices found". Also, "The volume control did not find any elemnets and/or devices to control. This means either that oyu do not have the right GStreamer plugins installed, or that oyu don not have a sound card configured."

Someone has kindly offered a manual solution to try and fix this problem, explaining that it was a common bug in Dapper that has since been fixed. The manual solution (my earlier posts) involved blacklisting the incorrect drivers and telling some other drivers to boot instead at startup:

> This is an old bug from the Dapper days. You can correct the problem by upgrading to Edgy or Feisty or you can fix it manually. I'll tell you how to fix it here, if that's what you want to do.

Unfortunately your sound card is incorrectly identified. You will need to switch which driver gets loaded despite what the PCI ID indicates.

You will need to blacklist the incorrect driver and force the correct one to load at boot time.

Open /etc/modprobe.d/blacklist:
Code:

sudo gedit /etc/modprobe.d/blacklist

scroll down to the bottom of the file and add these two lines:
Code:

blacklist snd-cs46xx
blacklist cs46xx

Open /etc/modprobe.d/alsa-base:
Code:

sudo gedit /etc/modprobe.d/alsa-base

and add the following lines to the end of the file:
Code:

alias char-major-116 snd
alias char-major-14 soundcore
alias snd-card-0 snd-cs4236
options snd-cs4236 isapnp=0 cport=0x538 port=0x530 sb_port=0x220 fm_port=0x388 irq=5 dma1=1 dma2=0
alias sound-slot-0 snd-card-0
alias sound-slot-1 snd-card-1

alias sound-service-0-0 snd-mixer-oss
alias sound-service-0-1 snd-seq-oss
alias sound-service-0-3 snd-pcm-oss
alias sound-service-0-8 snd-seq-oss
alias sound-service-0-12 snd-pcm-oss

alias /dev/mixer snd-mixer-oss
alias /dev/dsp snd-pcm-oss
alias /dev/midi snd-seq-oss

options snd cards_limit=1

Open the file /etc/modules:
Code:

sudo gedit /etc/modules

And add this line to the end of the file:
Code:

snd-cs4236




This, sadly, did not work. 

I then decided to upgrade to 6.10 (Edgy) using the alternate install cd. That was last night. Unfortunately, the problem persists. 

lspci reveals:

> 00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:02.0 CardBus bridge: Texas Instruments PCI1251A
00:02.1 CardBus bridge: Texas Instruments PCI1251A
00:06.0 Multimedia audio controller: Cirrus Logic CS 4610/11 [CrystalClear SoundFusion Audio Accelerator] (rev 01)
00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
01:00.0 VGA compatible controller: Neomagic Corporation NM2200 [MagicGraph 256AV] (rev 20)
02:00.0 Ethernet controller: Xircom Cardbus Ethernet 10/100 (rev 03)


Does anyone have any ideas on how I may fix this?

I am really new to linux and command line...but i'll try anything.

Sorry for the length of the post. 

Thanks for your help.

---

### Post by mahy on 2007-05-17
Can you get connected? Then open Synaptic and install everything beginning with "gstreamer" and "libgstreamer". It's really easy, no command line necessary.

---

### Post by whoKnew on 2007-05-17
actually, i don't have a working connection with my linux box just yet. i'm still wifi card shopping.
is there somewhere i can find all these files on my windows pc and transfer them over?

---

### Post by Mowog on 2007-05-19
I've recently adopted Ubuntu, and am having the same issue with sound... or lack of same. I have a Creative X-Fi Extreme Music sound card, and my research so far has led me to the GStreamer plugins. Based on advice given in another thread, I found and installed those plugins, but still have no audio.

Just to make sure I'm doing this right, I've gone to Applications --> Add/Remove --> Sound & Video, and have verified that all the recommended GStreamer drivers are listed and checked. I then click OK, but nothing seems to change, even after a restart.

So I'll join the list of folks looking for an audio solution. I've installed Audacity for Ubuntu; I use Windows Audacity quite a bit for recording and editing material The Cavern Today podcast, and I'd like to give it a try in Ubuntu also.

Thanks!

Mowog

---


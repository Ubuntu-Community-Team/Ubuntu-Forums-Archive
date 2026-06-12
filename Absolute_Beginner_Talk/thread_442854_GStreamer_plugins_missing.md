---
title: "GStreamer plugins missing"
date: 2007-05-13
forum: Absolute Beginner Talk
---

### Post by whoKnew on 2007-05-13
Hi Everyone.

I just got ubuntu a few days ago (linux/ubuntu newbie..if that helps),
and I realized that no sounds will play from my computer. there is an X on the speaker logo on the toolbar.

when i try accessing it, i get this message:
"No volume control. GStreamer plugins and/or devices found".

So i'm assuming that i'm missing some kind of audio drivers.
I am wondering if there is an easy way to find out which drivers I need. I feel like there are a lot of different ones to choose from and I'm not quite sure how to tell which ones my system is lacking. I'm kind of new to command line...

I have an ibm thinkpad 600e. running Dapper Drake 6.06.

lspci yields:

0000:00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
0000:00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
0000:00:02.0 CardBus bridge: Texas Instruments PCI1251A
0000:00:02.1 CardBus bridge: Texas Instruments PCI1251A
0000:00:06.0 Multimedia audio controller: Cirrus Logic CS 4610/11 [CrystalClear SoundFusion Audio Accelerator] (rev 01)
0000:00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
0000:00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
0000:00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
0000:00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
0000:01:00.0 VGA compatible controller: Neomagic Corporation NM2200 [MagicGraph 256AV] (rev 20)
0000:02:00.0 Ethernet controller: Xircom Cardbus Ethernet 10/100 (rev 03)

and that's about it .

any help is greatly appreciated. thanks!

:: wK

---

### Post by benanzo on 2007-05-13
This is an old bug from the Dapper days.  You can correct the problem by upgrading to Edgy or Feisty or you can fix it manually.  I'll tell you how to fix it here, if that's what you want to do.

Unfortunately your sound card is incorrectly identified.  You will need to switch which driver gets loaded despite what the PCI ID indicates.

You will need to blacklist the incorrect driver and force the correct one to load at boot time.

Open /etc/modprobe.d/blacklist:
```
sudo gedit /etc/modprobe.d/blacklist
```
scroll down to the bottom of the file and add these two lines:
```

blacklist snd-cs46xx
blacklist cs46xx

```

Open /etc/modprobe.d/alsa-base:
```
sudo gedit /etc/modprobe.d/alsa-base
```

and add the following lines to the end of the file:
```
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
```

Open the file /etc/modules:
```
sudo gedit /etc/modules
```
And add this line to the end of the file:
```
snd-cs4236
```

Reboot for the changes to take effect.

---

### Post by whoKnew on 2007-05-14
thanks for the reply!

sadly, i've tried the above solution three different times (finding code errors in my transcription the first two times), and it doesn't seem to work. the process seems to make sense, as much as i can understand it...but now i think i'm back to square one. 
is there another solution aside from upgrading?

i'm going to keep at it...

---

### Post by whoKnew on 2007-05-14
here is the feedback that the terminal gives me throughout the process:

(i have to include it as an attachment because apparently i'm including images?)

i hope that helps?

thanks for your time.

---

### Post by benanzo on 2007-05-15
If I remember correctly you might need to disable Fastboot in your BIOS settings.  For some reason Fastboot can tell ALSA that your sound hardware is unaccessible/non-existent.  I'm pretty sure this bug has been fixed since Dapper.

---


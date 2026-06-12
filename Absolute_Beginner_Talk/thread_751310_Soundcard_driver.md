---
title: "Soundcard driver?"
date: 2008-04-10
forum: Absolute Beginner Talk
---

### Post by Calixte on 2008-04-10
I have been using Ubuntu for a while now and basically, I have only one problem: whenever my computer plays a sound (e.g. music, notifivation, logon, etc.) I get a verry high piched sound in the background. Playing with the Gain resolves my problem (sometimes) bt sound generally dissapears after the operation which leaves me with less than i had in the begining. I found no way of correcting the second problem but to reinstall ubuntu.
Can the problem (the first one) be fixed or is my soundcard uncompartible with the ubuntu drivers? in the second case, i would have no problem buying a new one, but I'd like to know how i could find out which sondcards are ubuntu-compatible
thanks for the effort,
Calixte

---

### Post by Ptero-4 on 2008-04-10
Does your card use the snd-hda-intel driver? If so you might want to try the model=3stack (for laptops) or model=5stack (some desktops) in the /etc/modprobe.d/alsa-base file.

---

### Post by stchman on 2008-04-10
> **Calixte said:**
> I have been using Ubuntu for a while now and basically, I have only one problem: whenever my computer plays a sound (e.g. music, notifivation, logon, etc.) I get a verry high piched sound in the background. Playing with the Gain resolves my problem (sometimes) bt sound generally dissapears after the operation which leaves me with less than i had in the begining. I found no way of correcting the second problem but to reinstall ubuntu.
Can the problem (the first one) be fixed or is my soundcard uncompartible with the ubuntu drivers? in the second case, i would have no problem buying a new one, but I'd like to know how i could find out which sondcards are ubuntu-compatible
thanks for the effort,
Calixte

What kind of sound card do you have right now?  I am assuming it is a desktop computer and not a laptop.

I have both an Audigy 2 and an older Live that work perfectly.  The X-Fi cards are not yet supported so I would recommend an Audigy card.

---

### Post by Calixte on 2008-04-11
I'm not really sure about which soundcard I have. Where can I check that?

For information (If that is any use) the "/etc/modprobe.d/alsa-base" sais this:

```
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe --quiet snd-ioctl32 ; : ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm && { /sbin/modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer && { /sbin/modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq && { /sbin/modprobe --quiet snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi && { /sbin/modprobe --quiet snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options cx88-alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
```

thanks for your help!
 - Calixte

PS: Yes it is a desktop ;-).

---

### Post by herbster on 2008-04-11
Paste the output of

```
lspci
```

---

### Post by stchman on 2008-04-11
> **Calixte said:**
> I'm not really sure about which soundcard I have. Where can I check that?

For information (If that is any use) the "/etc/modprobe.d/alsa-base" sais this:

```
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe --quiet snd-ioctl32 ; : ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm && { /sbin/modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer && { /sbin/modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq && { /sbin/modprobe --quiet snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi && { /sbin/modprobe --quiet snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options cx88-alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
```

thanks for your help!
 - Calixte

PS: Yes it is a desktop ;-).

From the output you pasted it looks like you have 2 soundcards installed.  It looks like a Creative Live or Audigy and the onboard VIA VT82xx.  I would like to see an output of lspci to make a final determination.

---

### Post by herbster on 2008-04-11
You gotta disable your onboard sound in the BIOS.

---

### Post by Calixte on 2008-04-12
```
calixte@Pauline:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. PT890 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
00:00.5 PIC: VIA Technologies, Inc. PT894 I/O APIC Interrupt Controller
00:00.7 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:02.0 PCI bridge: VIA Technologies, Inc. PT890 PCI to PCI Bridge Controller
00:0f.0 IDE interface: VIA Technologies, Inc. VT8237A SATA 2-Port Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237A PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
00:13.0 PCI bridge: VIA Technologies, Inc. VT8237A Host Bridge
00:13.1 PCI bridge: VIA Technologies, Inc. VT8237A PCI to PCI Bridge
02:00.0 VGA compatible controller: nVidia Corporation NV44 [GeForce 6200 TurboCache(TM)] (rev a1)
03:01.0 Audio device: VIA Technologies, Inc. VIA High Definition Audio Controller (rev 10)
04:04.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)
04:05.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 61)

```

---

### Post by Calixte on 2008-04-12
PS: Didn't find any "Onboard Sound" in my BIOS > v02.58 (C) Copyright 1958-2006, American Megatrends, Inc.

---

### Post by herbster on 2008-04-12
```
lsmod | grep snd
```

Paste the output.

---

### Post by Calixte on 2008-04-13
```
calixte@Pauline:~$ lsmod | grep snd
snd_hda_intel         263712  1 
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54660  11 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm

```
 Thanks forr the help

---

### Post by herbster on 2008-04-14
That sound device is definitely supported. Will perhaps need some tweaking. Run

```
speaker-test -c2 -twav -Ddefault
```

And paste the output whether you hear the voice or there is an error. Hit CTRL+C to end the test at any time.

---

### Post by Calixte on 2008-04-14
I just hear "front right", a high pitched sound is continually emitted from the left speaker
It does this with any sound system I have. Can it be a problem with my sound card?

thanks for your help,
Calixte

---

### Post by herbster on 2008-04-17
Does it do the same in Windows? Are you able to boot into Windows?

---

### Post by Calixte on 2008-04-18
The sound works perfectly on XP (not on Vista though, I dont even have sound on that £%*¨ù*§ OS)

---

### Post by Calixte on 2008-04-23
PS: I did not update my Vista, so that may be the problem with it. 
I have Ubuntu since 6.04, and the problem has always been the same. Do i have to buy a new sound card? if so, could you help? I have no experience in building my own computer except for a wifi I have addedonce.

---

### Post by herbster on 2008-04-23
Calixte, do you know how to use IRC? The Alsa channel on Freenode is probably your best bet, guaranteed some expert in there could get it to work.

---


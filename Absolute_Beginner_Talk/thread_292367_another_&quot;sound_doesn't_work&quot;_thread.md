---
title: "another &quot;sound doesn't work&quot; thread"
date: 2006-11-03
forum: Absolute Beginner Talk
---

### Post by Caligula on 2006-11-03
yeah. i've finally come to this. after months of using various distros, on various machines. I've finally gotten to the point of where my sound doesn't work. ain't it great?

so yeah, it's kind of a debian question, please forgive me, i'm addicted to these forums so i'll ask here :) 

I've just installed debian etch, everything seems to work ok, except that no sound can be heard from the system, nothing. I have absolutely no idea how to solve that kind of thing as I never had problems with sound. 

The lspci output is: 
```
lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133] (rev 81)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133 AGP]
00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 40)
00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1a)
00:07.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1a)
00:07.4 Host bridge: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 40)
00:07.5 Multimedia audio controller: VIA Technologies, Inc. VT82C686 AC97 Audio Controller (rev 50)
00:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:00.0 VGA compatible controller: nVidia Corporation NV15 [GeForce2 GTS/Pro] (rev a3)

```

And here's some more details about the audio bit, i don't understand a word there. ](*,) 
```
00:07.5 Multimedia audio controller: VIA Technologies, Inc. VT82C686 AC97 Audio
Controller (rev 50)
        Subsystem: Micro-Star International Co., Ltd. Unknown device 3400
        Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Step
ping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort
- <MAbort- >SERR- <PERR-
        Interrupt: pin C routed to IRQ 10
        Region 0: I/O ports at dc00 [size=256]
        Region 1: I/O ports at e000 [size=4]
        Region 2: I/O ports at e400 [size=4]
        Capabilities: <access denied>
00: 06 11 58 30 01 00 10 02 50 00 01 04 00 00 00 00
10: 01 dc 00 00 01 e0 00 00 01 e4 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 62 14 00 34
30: 00 00 00 00 c0 00 00 00 00 00 00 00 0a 03 00 00

```

If anyone could point me to the right direction I'll be forever greatfull :-D 

and by the way, on ubuntu the sound worked perfectly out of the box, so I know there has to be a way[-( 

Thanks :D 


:confused:


EDIT:

and also, the output of lsmod | grep snd is:

snd_via82xx            25368  1
gameport               13704  1 snd_via82xx
snd_ac97_codec         82848  1 snd_via82xx
snd_ac97_bus            2304  1 snd_ac97_codec
snd_pcm                74376  2 snd_via82xx,snd_ac97_codec
snd_timer              20484  1 snd_pcm
snd_page_alloc          9992  2 snd_via82xx,snd_pcm
snd_mpu401_uart         6784  1 snd_via82xx
snd_rawmidi            22304  1 snd_mpu401_uart
snd_seq_device          8460  1 snd_rawmidi
snd                    46336  9 snd_via82xx,snd_ac97_codec,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore               8928  1 snd

---

### Post by bettlebrox on 2006-11-03
Try running alsaconf as root (or using sudo).

Also, sometimes people have this problem and the sound levels are set to zero. Try using aumix or alsamixer and look at the volume settings.

Luck!

---

### Post by Caligula on 2006-11-03
THANKS! solved it :]
I'm gonna have to live and see if it'll work from now on, but it looks alright :]

---

### Post by bettlebrox on 2006-11-03
>THANKS! solved it :]
Great! :)

Can you tell us what worked? Might help someone else in the futire.

---

### Post by Caligula on 2006-11-03
the alsaconf has solved it :]
It found two sound cards or something, i chose one and it loaded the driver for it and now all is working.

---

### Post by hyby on 2006-11-03
congratulations...i envy your success. 

I for one have sturggled because i believe one of my audio codecs has no been covered by ALSA, by the signs of things.

Again, congratulations.

---

### Post by bettlebrox on 2006-11-05
hyby what issues are you having with your card? Have you asked on the forums?

---


---
title: "lsmod | grep sndfunction snd_ctl_open failed for default: No such device"
date: 2007-07-23
forum: Absolute Beginner Talk
---

### Post by finovial on 2007-07-23
How the hell do I fix this?!?! I've uninstalled and reinstalled ALSA many times, and I can't use Alsamixer, and I don't get any sound.

I want to use my Sound Blaster Audigy 2 ZS, and it's apparently supported by ALSA, but I simply can't get this crap to work.

 I followed the noob guide for fixing sound, and that didn't work. I'll paste all of my outputs down here:


aplay -l

```
**** List of PLAYBACK Hardware Devices ****
card 0: Audigy2 [Audigy 2 ZS [SB0350]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
card 0: Audigy2 [Audigy 2 ZS [SB0350]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
card 0: Audigy2 [Audigy 2 ZS [SB0350]], device 3: emu10k1 [Multichannel Playback]
card 0: Audigy2 [Audigy 2 ZS [SB0350]], device 4: p16v [p16v]
card 1: Headset [Plantronics Headset], device 0: USB Audio [USB Audio]

```


lspci -v

```
00:0a.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
        Subsystem: Creative Labs SB Audigy 2 ZS (SB0350)
        Flags: bus master, medium devsel, latency 32, IRQ 22
        I/O ports at e200 [size=64]
        Capabilities: <access denied>

00:0a.1 Input device controller: Creative Labs SB Audigy Game Port (rev 04)
        Subsystem: Creative Labs SB Audigy MIDI/Game Port
        Flags: bus master, medium devsel, latency 32
        I/O ports at e800 [size=8]
        Capabilities: <access denied>

00:0a.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 04) (prog-if 10 [OHCI])
        Subsystem: Creative Labs SB Audigy FireWire Port
        Flags: bus master, medium devsel, latency 32, IRQ 17
        Memory at f3027000 (32-bit, non-prefetchable) [size=2K]
        Memory at f3020000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
```


sudo modprobe snd-

```
snd-ac97-codec      snd-cs8427          snd-indigoio        snd-sb16
snd-ad1816a         snd-darla20         snd-intel8x0        snd-sb16-csp
snd-ad1848          snd-darla24         snd-intel8x0m       snd-sb16-dsp
snd-ad1848-lib      snd-dt019x          snd-interwave       snd-sb8
snd-ad1889          snd-dummy           snd-interwave-stb   snd-sb8-dsp
snd-adlib           snd-echo3g          snd-korg1212        snd-sbawe
snd-ainstr-fm       snd-emu10k1         snd-layla20         snd-sb-common
snd-ainstr-gf1      snd-emu10k1-synth   snd-layla24         snd-seq
snd-ainstr-iw       snd-emu10k1x        snd-maestro3        snd-seq-device
snd-ainstr-simple   snd-emu8000-synth   snd-mia             snd-seq-dummy
snd-ak4114          snd-emux-synth      snd-miro            snd-seq-instr
snd-ak4117          snd-ens1370         snd-mixart          snd-seq-midi
snd-ak4531-codec    snd-ens1371         snd-mixer-oss       snd-seq-midi-emul
snd-ak4xxx-adda     snd-es1688          snd-mona            snd-seq-midi-event
snd-ali5451         snd-es1688-lib      snd-mpu401          snd-seq-oss
snd-als100          snd-es18xx          snd-mpu401-uart     snd-seq-virmidi
snd-als300          snd-es1938          snd-mtpav           snd-serial-u16550
snd-als4000         snd-es1968          snd-mts64           snd-sgalaxy
snd-atiixp          snd-es968           snd-nm256           snd-sonicvibes
snd-atiixp-modem    snd-fm801           snd-opl3-lib        snd-sscape
snd-au8810          snd-gina20          snd-opl3sa2         snd-tea575x-tuner
snd-au8820          snd-gina24          snd-opl3-synth      snd-tea6330t
snd-au8830          snd-gusclassic      snd-opl4-lib        snd-timer
snd-azt2320         snd-gusextreme      snd-opl4-synth      snd-trident
snd-azt3328         snd-gus-lib         snd-opti92x-ad1848  snd-trident-synth
snd-bt87x           snd-gusmax          snd-opti92x-cs4231  snd-usb-audio
snd-bt-sco          snd-gus-synth       snd-opti93x         snd-usb-lib
snd-ca0106          snd-hda-codec       snd-page-alloc      snd-usb-usx2y
snd-cmi8330         snd-hda-intel       snd-pcm             snd-util-mem
snd-cmipci          snd-hdsp            snd-pcm-oss         snd-via82xx
snd-cs4231          snd-hdspm           snd-pcxhr           snd-via82xx-modem
snd-cs4231-lib      snd-hwdep           snd-pdaudiocf       snd-virmidi
snd-cs4232          snd-i2c             snd-rawmidi         snd-vx222
snd-cs4236          snd-ice1712         snd-riptide         snd-vx-lib
snd-cs4236-lib      snd-ice1724         snd-rme32           snd-vxpocket
snd-cs4281          snd-ice17xx-ak4xxx  snd-rme96           snd-wavefront
snd-cs46xx          snd-indigo          snd-rme9652         snd-ymfpci
snd-cs5535audio     snd-indigodj        snd-rtctimer        
```





No matter what, I keep getting "alsamixer: function snd_ctl_open failed for default: No such device" when trying to use alsamixer.

Someone PLEASE help me!

---

### Post by sad_iq on 2007-07-23
Don't have this card..and the thing that get's me wondering is  **card 1: Headset [Plantronics Headset], device 0: USB Audio [USB Audio]** Make sure that doesn't interfere with your sound card...go to system -> preference -> sound and see if ubuntu chooses the wright sound card or the headset...Can't do much to help...but I'll try!!!

---

### Post by finovial on 2007-07-23
> **sad_iq said:**
> Don't have this card..and the thing that get's me wondering is  **card 1: Headset [Plantronics Headset], device 0: USB Audio [USB Audio]** Make sure that doesn't interfere with your sound card...go to system -> preference -> sound and see if ubuntu chooses the wright sound card or the headset...Can't do much to help...but I'll try!!!

I unplugged the headset, and I still get the same problem. Also, when I try to test the ALSA device/Audigy, it says "audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=music: Could not open resource for writing"

---

### Post by lazyrussian on 2007-11-23
I have this exact same problem with my SB450 (I'm guessing SB - Sound Blaster)

I've spent a good part of the afternoon recompiling all the necessary alsa stuff from source, but now I get this error. If I find anything I'll post back.

---

### Post by lazyrussian on 2007-11-23
Ok, I fixed aprt of this problem.

Go to synaptic and install alsamixergui + reinstall the alsa source/utils/lib.

I rebooted and alsa mixer started working.

---


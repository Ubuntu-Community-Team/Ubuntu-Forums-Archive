---
title: "Sound issues using Edirol UA25 and Macbook.  Please help me!"
date: 2008-11-13
forum: Apple Hardware Users
---

### Post by alexdelay on 2008-11-13
[FONT="Verdana"]Hi there

I have an audio problem and was hoping there is someone that could provide some insight

I use a Korg synthesiser which is plugged into the inputs of the sound card

The outputs are fed through my speakers.  The device is connected via usb

I am able to here sound out the speakers only IF I play a file on the macbook already

When I attempt to play a sound on my Korg I hear nothing :(

I have reinstalled the drivers, I have changed the audio IN/OUT to the correct soundcard ie UA25 in system preferences and I have also chosen edirol as my main sound drivers in the software I use for recording my live sets

It Has previously worked until one day I disconnected everything when I moved home, since then I can listen to online radio stations or itunes fine however there is no sound when I play my korg and no outputs are recognised either in the software....the levels are flat

It must be something Im doing wrong.  I have a similar problem with my USB broadband modem in the sense that I need to reinstall the drivers every time I shut down

If anyone has the time to respond with their ideas I would appreciate it

Alex/FONT]

---

### Post by Quaestor23 on 2009-12-27
Hi
I know this is an ancient thread but thought I'd reply in case anyone else finds this through Google. 

I use Debian rather than Ubuntu but it's the same thing, and I've never had any problem with this device, it works brilliantly in Linux.

First thing to do with any problem of this kind is to run [FONT=monospace]**[SIZE=5]aplay -l[/SIZE]**[/FONT] and [FONT=monospace]**[SIZE=5]arecord -l[/SIZE]**[/FONT] in a terminal. This lists the available ALSA output and input devices respectively. 

The UA-25 is only a duplex device (that is, provides both inputs and outputs simultaneously) when the Advance switch is OFF. In this mode, i/o is fixed at 44.1kHz 16-bit. Output goes to both analog and digital outputs, input is switched according to the front-panel Digital In switch.

When the Advance switch is ON, the UA-25 only provides [SIZE=3]*either* input *or* output[/SIZE], depending on whether the Rec/Play switch is pressed, at the bitrate selected by the switch on the back. AIUI, this is not a weakness of the UA-25, it's a limitation of the speed that can be achieved over USB 2.0 - it's not fast enough to support 24x96 in both directions. You need Firewire for that.

So one possibility is that you were inadvertantly in Advance mode.

Another is that you had the Digital In switch pressed, which disables the analogue inputs in favour of the optical digital. 

And, of course, make absolutely sure that your software is using the right device. Also check that there's nothing odd in your ~/.asoundrc which might be interfering.

Don't forget that if you change any setting on ther UA-25, you need to reboot it. If USB-powered, disconnecting from USB and reconnecting will suffice. If using the external power adapter, you may have to pull that too (not sure, never used it myself). 

It's very unlikely to be any problem with drivers/software, because afaik there is no soft control of the UA-25 *at all*, not even a volume control - the hardware switches, buttons and knobs are the only controls available. 

If the UA-25 is not showing up in [FONT=monospace]**[SIZE=5]aplay -l[/SIZE]**[/FONT] and [FONT=monospace]**[SIZE=5]arecord -l[/SIZE]**[/FONT] at all, then it hasn't been detected properly. Try unplugging and replugging while you tail the output of /var/log/messages, see what the kernel says about it. This is what mine says when it's plugged in:

```

Dec 27 20:52:11 fermi kernel: usb 2-2: new full speed USB device using ohci_hcd and address 3
Dec 27 20:52:11 fermi kernel: usb 2-2: New USB device found, idVendor=0582, idProduct=0073
Dec 27 20:52:11 fermi kernel: usb 2-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
Dec 27 20:52:11 fermi kernel: usb 2-2: Product: EDIROL UA-25
Dec 27 20:52:11 fermi kernel: usb 2-2: Manufacturer: Roland
Dec 27 20:52:11 fermi kernel: usb 2-2: configuration #1 chosen from 1 choice

```Use [FONT="monospace"]**[SIZE=5]lsmod[/SIZE]**[/FONT] to confirm that the snd-usb-audio module is loaded. You should also be able to see the device in the output of [FONT="monospace"]**[SIZE=5]lsusb[/SIZE]**[/FONT], eg:
```
Bus 002 Device 003: ID 0582:0073 Roland Corp. EDIROL UA-25
```Here's my [FONT="monospace"]**[SIZE=5]lsmod|grep snd[/SIZE]**[/FONT]. The intel8x0 and related are my motherboard's onboard audio.
```

snd_intel8x0           29392  1 
snd_ac97_codec         99412  1 snd_intel8x0
snd_usb_audio          79872  1 
ac97_bus                1300  1 snd_ac97_codec
snd_pcm_oss            36096  0 
snd_mixer_oss          16340  1 snd_pcm_oss
snd_pcm                63388  5 snd_intel8x0,snd_ac97_codec,snd_usb_audio,snd_pcm_oss
snd_usb_lib            15284  1 snd_usb_audio
snd_seq_dummy           2424  0 
snd_seq_oss            27264  0 
snd_hwdep               6808  1 snd_usb_audio
snd_seq_midi            6208  0 
snd_rawmidi            20192  2 snd_usb_lib,snd_seq_midi
snd_seq_midi_event      6196  2 snd_seq_oss,snd_seq_midi
snd_seq                46096  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19800  2 snd_pcm,snd_seq
snd_seq_device          6144  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    51396  16 snd_intel8x0,snd_ac97_codec,snd_usb_audio,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_hwdep,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               6144  1 snd
snd_page_alloc          8028  2 snd_intel8x0,snd_pcm
usbcore               134928  7 usb_storage,usb_libusual,snd_usb_audio,snd_usb_lib,ohci_hcd,ehci_hcd

```

---


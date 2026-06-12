---
title: "Creative Vibra128 Sound Card - No sound!"
date: 2008-04-10
forum: Absolute Beginner Talk
---

### Post by velocity99 on 2008-04-10
Hi Guys,

My first post, please forgive anything obvious that I may have missed...

I've installed Ubuntu 7.10 Gutsy Gibbon on my Athlon 1.4 - 512RAM - 320GB-WD HDD on an old ASUS mobo.

I have a PCI Creative Vibra 128 Sound card in it as the mobo doesn't have onboard sound, the card works no problem with windows, however no cigar with Ubuntu - I used to have FC4 and FC5 installed on this box, and it didn't work for either of them also.

Results of lspci -v are as follows...

           [B]  00:0b.0 Multimedia audio controller: Creative Labs Ectiva EV1938
             Subsystem: Creative Labs Unknown device 5938
             Flags: bus master, slow devsel, latency 32, IRQ 11
             I/O ports at 9400 [size=64]
             I/O ports at 9000 [size=32]
             Capabilities: <access denied>[/B]

Ubuntu can see the device, however not sure about the Subsystem or the Capabilities - Are these critical for sound output ?

Under Sound Preferences, Devices, Sound Events, Sound Playback is set to autodetect.
Under Sounds, Enable Software Sound Mixing (ESD) is ticked, along with play system sounds.

I have speakers plugged in that are turned on and the volume is up.

If I'm not able to fix it via drivers / system configs, might the best option to be source another PCI soundcard ?

Any and all help very much appreciated    =)

Cheers,

Velocity99

---

### Post by nugencs on 2008-04-10
Hi! Perhaps this info might work: [http://frodo.syminet.com/~deep/vibralin.html]("http://frodo.syminet.com/~deep/vibralin.html")

---


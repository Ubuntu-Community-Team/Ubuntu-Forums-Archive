---
title: "Wierd problem with music cd"
date: 2005-02-15
forum: Apple PPC Users
---

### Post by kris kincaid on 2005-02-15
Hello,

I have Ubuntu installed on a G3 Lombard Powerbook. I was trying to see if it would play a manufactured music CD, and it didn't work.  ](*,) 

Anyway, I left the cd in the drive. On the next reboot, it paused for about a minute on "Loading Modules", then it moved on. That was odd, but I ignored it. Then I tried to dial to the internet, and I kept getting bumped off line. I looked up the PPPD exit code  and it said:

> The kernel does not support PPP, for  example,  the PPP  kernel  driver  is  not  included or cannot be loaded.
  

After I ejected the CD from the drive, then rebooted everything worked fine. I was able to connect to the ISP and it boots much faster.

Bizarre.  :-(

---

### Post by fu. on 2005-02-15
hmmm, that really sound weird...

sound/audio problems are common with Warty but i never heard before that a conflict with the audio would block the internal modem...

what i do know so far is that NewWorld machines have no audio connection between their CD-ROM drive and their sound hardware. Therefore, audio information must be read as data and then piped to the sound hardware. This is possible using xmms and the xmms-cdread plugin, that reads the audio off the CD over the ATA cable, decodes it in software and sends it to the sound card over the PCI bus as digital data. If you want 'true' cd-playing, you have to enable some SCSI options in the kernel: 

```
SCSI emulation support, 
SCSI support, 
SCSI CD-ROM support
```

---

### Post by chascon on 2005-03-09
"Therefore, audio information must be read as data and then piped to the sound hardware. This is possible using xmms and the xmms-cdread plugin, that reads the audio off the CD over the ATA cable, decodes it in software and sends it to the sound card"

actuality it is  "CD Audio Player  [libcdaudio.so]"
and configure the plugin as so ... Device/ enable Digital Audio Extraction
(This is for xmms.)  

The default CD player is fixed in hoary.

---


---
title: "Installing Ubuntu onto Acer 9301AWSMi"
date: 2007-05-30
forum: Absolute Beginner Talk
---

### Post by njknight on 2007-05-30
Hi to the group - I'm considering an installation of Ubuntu onto my Acer Aspire 9301AWSMi laptop - to replace Vista (which runs so slow).  Has anyone got any experience of installing Ubunto onto this model of laptop and if so any gems of advice would be much appreciated. ( Running Ubunto from the CDROM seems to be no problem with the exception that the laptop sound system no longer works !)

---

### Post by wpshooter on 2007-05-30
From what I have read on this forum, I would think that if your sound is not working properly on the live CD then it is probably not going to work when installed on your hard drive and you are going to have to find a solution to that (if you are lucky).

---

### Post by ugm6hr on 2007-05-30
> **njknight said:**
> Hi to the group - I'm considering an installation of Ubuntu onto my Acer Aspire 9301AWSMi laptop - to replace Vista (which runs so slow).  Has anyone got any experience of installing Ubunto onto this model of laptop and if so any gems of advice would be much appreciated. ( Running Ubunto from the CDROM seems to be no problem with the exception that the laptop sound system no longer works !)

If the LiveCD works - then installing should be a breeze.  

It might be worthwhile trying to sort the sound issue out before installing, if that particularly worries you.  I had a similar Vista experience with my Acer 5051AWXMi, and ended up with Xubuntu7.04.  My laptop has a slightly different Realtek Audio chipset, but my solution is worth trying.

In Terminal (in Applications->Accessories, I think), enter
*alsamixer* and press Enter
This loads the sound controller thing (don't worry - if you want a more visually pleasing version, theres GNOME Alsa MIxer for you to use later).
Use the left/right arrows to move between different sound outputs/inputs, and up/down arrows to increase/decrease each volume.  Press "m" to turn mute on (MM) / off (OO) for each output.  On my laptop - I just muted the "Front" speaker, and unmuted and turned up the "Surround" volume.  It should then work (although it's hard to try because of the lack of mp3 support as default).

---

### Post by njknight on 2007-05-30
Thanks for your comment - I've trawled the net, and there just doesn't seem to be many people who have tried to install onto this particular laptop, but I'm not going to necessarily give in at the first hurdle.

---

### Post by oilchangeguy on 2007-05-30
since 7.04 was released there have been many posts about sound problems. you might also try version 6.06, as it's the lts (long term support) version.

---

### Post by njknight on 2007-05-30
many thanks to ugm6hr, oilchangeguy and wpshooter- I'll take your advice and try these suggestions to see where we go from there.  If I find any success then I'll post back to the group.

---

### Post by bigspottycat on 2007-05-30
I installed Feisty onto my Acer Aspire 5602 WLMi with no real problems; pretty much everything worked 'out of the box' and was a much easier install than either Dapper or Edgy. I haven't been able to get the built-in camera or bluetooth to work, although I haven't spent much time trying yet. The sound worked automatically for me...

---

### Post by njknight on 2007-05-31
ugm6hr - your suggestion worked a treat and I can indeed now get sound ou of the Acer Aspire 9301ASMi - excellent stuff and many thanks for that tip - now that just leaves me the built in web cam and the media slots - then it's good bye to Windows Vista

---

### Post by ugm6hr on 2007-05-31
> **njknight said:**
> ugm6hr - your suggestion worked a treat and I can indeed now get sound ou of the Acer Aspire 9301ASMi - excellent stuff and many thanks for that tip - now that just leaves me the built in web cam and the media slots - then it's good bye to Windows Vista

Glad that worked.  

As for the media slots - you may be out of luck.  Acer have been using ENE media card readers in recent times, and they just don't work with Linux (no driver support).  You can check by entering *lspci* in Terminal.  If you get anything that looks like this, you're unlikely to succeed.

```

08:01.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
08:01.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
08:01.2 Generic system peripheral [0805]: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01)
08:01.3 FLASH memory: ENE Technology Inc FLASH memory: ENE Technology Inc: (rev 01)
08:01.4 FLASH memory: ENE Technology Inc Unknown device 0551 (rev 01)

```

---

### Post by samjam on 2007-06-26
> **ugm6hr said:**
> If the LiveCD works - then installing should be a breeze.  

It might be worthwhile trying to sort the sound issue out before installing, if that particularly worries you.  I had a similar Vista experience with my Acer 5051AWXMi, and ended up with Xubuntu7.04.  My laptop has a slightly different Realtek Audio chipset, but my solution is worth trying.

In Terminal (in Applications->Accessories, I think), enter
*alsamixer* and press Enter
This loads the sound controller thing (don't worry - if you want a more visually pleasing version, theres GNOME Alsa MIxer for you to use later).
Use the left/right arrows to move between different sound outputs/inputs, and up/down arrows to increase/decrease each volume.  Press "m" to turn mute on (MM) / off (OO) for each output.  On my laptop - I just muted the "Front" speaker, and unmuted and turned up the "Surround" volume.  It should then work (although it's hard to try because of the lack of mp3 support as default).

I can confirm that this got audio working on my Aspire 9301AWSMi (350.00 UKP refurbished from PC World website).

Thanks for posting this audio help.

My card reader is: 04:06.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)

Just got to get the webcam working....

Sam

---


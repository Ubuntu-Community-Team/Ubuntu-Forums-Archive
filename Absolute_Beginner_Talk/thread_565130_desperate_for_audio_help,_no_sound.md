---
title: "desperate for audio help, no sound"
date: 2007-10-01
forum: Absolute Beginner Talk
---

### Post by silverace99 on 2007-10-01
I've been at it for a month now, hopefully someone here can lend me a hand :/

My problem is quite simply that I get no sound. There wasn't any when I first installed feisty fawn, and following the Ubuntu documentation troubleshooting has not solved my problem either.

For details, I run a laptop (acer Aspire), so I assume the sound card must be integrated with the mobo

following the documentation instructions for data collection, I got the following:

> cat /proc/asound/cards

 0 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xb0000000 irq 19


>  aplay --list-devices

**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


> lspci -v

00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)
        Subsystem: Acer Incorporated [ALI] Unknown device 010f
        Flags: bus master, slow devsel, latency 64, IRQ 19
        Memory at b0000000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>


If this is not enough information please let me know what else I need to look at!

---

### Post by Pumalite on 2007-10-01
[https://help.ubuntu.com/community/DebuggingSoundProblems](https://help.ubuntu.com/community/DebuggingSoundProblems)

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by silverace99 on 2007-10-01
yeah the first link was the one I had followed before

I went through the nice instructions on the second link......however I am still unable to output any sound. From what I can tell my card is supported by the alsa-project.

I don't suppose there might be any other suggestions, or ways that I can diagnose the problem :(

---

### Post by Pumalite on 2007-10-01
The only links I have. I'm not a great 'Sound Man'

---

### Post by CalvinK on 2007-10-02
> **silverace99 said:**
> I've been at it for a month now, hopefully someone here can lend me a hand :/

My problem is quite simply that I get no sound. There wasn't any when I first installed feisty fawn, and following the Ubuntu documentation troubleshooting has not solved my problem either.

For details, I run a laptop (acer Aspire), so I assume the sound card must be integrated with the mobo

following the documentation instructions for data collection, I got the following


If this is not enough information please let me know what else I need to look at!

You can test the following link for HDAIntel sound cards :
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

If it doesn't work go to [http://www.alsa-project.org/main/index.php/MainPage](http://www.alsa-project.org/main/index.php/MainPage), download the 
alsa-driver, lib and utils and follow the Howto at the same address and look for your  driver at the Sound card matrix. Then, if needed, apply the patch and add something at the end of /etc/modprobe.d/alsa-base (sudo gedit) at described in the previous link. I do not own the same laptop but I also have got a Intel Sound Card and worked a bit to have a functioning audio.
I hope it will help you:KS

---

### Post by silverace99 on 2007-10-04
Thanks CalivinK, ya I reinstalled the alsa drivers and made sure to explicitly tell it to use intel-hda

Now I have sound (oh beautiful, beautiful sound), but ONLY if I plug in headphones. If I unplug, no sound comes out of the built-in laptop speakers :(

Any idea why that might be the case?

---

### Post by odzk on 2007-10-04
did u check your comp manufacturer for the driver of your sound card. maybe they have some driver files for linux, they installing them if they have.

---

### Post by silverace99 on 2007-10-04
yes i checked, and no they do not have linux drivers

---


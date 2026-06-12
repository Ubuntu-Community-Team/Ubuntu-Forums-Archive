---
title: "Is there a conf file for soundcards? I keep loosing sound on reboot."
date: 2007-09-15
forum: Absolute Beginner Talk
---

### Post by ROUBOS on 2007-09-15
Hi people.
My sound worked fine after some driver install from Synaptic. (Audigy 2 zs) I just did a search for alsa and audigy and installed some drivers and it worked. 
Then after a restart there is no sound again why?

---

### Post by ROUBOS on 2007-09-15
When I use the command $ alsamixer it shoes Realtek as the device and not Audigy card.
That might be the problem? What's the config file in order to change it in?

---

### Post by ROUBOS on 2007-09-15
SOLVED. I entered BIOS and disabled the onboard sound card. Then ran the terminal again and the command $ alsamixer and changed the Analog/Digital output jack and it works
:):guitar:

---

### Post by Maestro23 on 2007-09-15
> **ROUBOS said:**
> SOLVED. I entered BIOS and disabled the onboard sound card. Then ran the terminal again and the command $ alsamixer and changed the Analog/Digital output jack and it works
:):guitar:

I was getting ready to say disable from BIOS.  Good deal man.:guitar:

---

### Post by ROUBOS on 2007-09-15
Hey sound works and all, but it's not the best sound. Alot of static type noise in the output. And it's not right. I have 2.1 speakers and they are not loud at all. Master and all is up. Don't know about the static like noise though.
Any thouhgts?

---

### Post by ROUBOS on 2007-09-15
apart from the sound not being the best, I restarted and there was no sound again. Entered alsamixer and the problems. Realtek showing instead of Audigy 2 zs.

I changed it in bios. Gonna check it again ;(

---

### Post by ROUBOS on 2007-09-15
OK restarted. AC'97 is DISABLED in BIOS. I don't get it.
Maybe I should uninstall all sound and let Ubuntu detect it again.

So how do I do that?

---

### Post by Maestro23 on 2007-09-15
> **ROUBOS said:**
> Hey sound works and all, but it's not the best sound. Alot of static type noise in the output. And it's not right. I have 2.1 speakers and they are not loud at all. Master and all is up. Don't know about the static like noise though.
Any thouhgts?

Hmm.. You got me there man.

---

### Post by kvonb on 2007-09-15
Have a look through this thread:

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by carusoswi on 2007-09-15
> **ROUBOS said:**
> Hi people.
My sound worked fine after some driver install from Synaptic. (Audigy 2 zs) I just did a search for alsa and audigy and installed some drivers and it worked. 
Then after a restart there is no sound again why?

What sort of computer do you have?
Your setup sounds very similar to mine.  The reboot problem is also similar to mine.  My 'puter is a small form factor XPC with the realtek onboard sound system.

I, too notice the reboot problem where my sound seems to switch configuration with every boot.  Disabling the realtek onboard sound should keep it from working after a reboot, so, I don't know what's happening there.  When you boot a third time and go into your bios, is the onboard sound still disabled?  If it is, then, I'm guessing that, when you complete boot, then, you have no sound at all, right?

I usually go into system, preferences, and just reset the sound from there.  On my system, the audigy driver is CA106.  Also, on my system, that driver is shown listed four times.  For things to work, I have to select the last instance of CA106 in the list for each setting (playback, etc).

Good luck.

Caruso

---

### Post by ROUBOS on 2007-09-15
My computer is:
AMD 64 3500+
2GB RAM
Audigy 2 ZS
300GB SATA Seagate
ATI RADEON X1950 pro 512mb
ASUS mobo

Running Ubuntu 32bit (had issues with 64bit)

Well I do have the onboard soundcard disabled in the BIOS, and when I reboot it's still disabled in BIOS but I don't get any sound in Ubuntu.
The alsamixer keeps re-setting and showing Realtek as the sound device and not my Audigy.
So my thoughts are, to remore both hardware and get Ubuntu to re-install just the Audigy card since the onboard one is Disable in BIOS and it should not detect it.

If only I knew how to do that

---

### Post by ROUBOS on 2007-09-15
I uninstalled the following from Synaptic:

alsa-base
alsa-firmware-loaders
ld10kl

I restarted and the sound works fine.
Should I re-install them?

---

### Post by ROUBOS on 2007-09-15
this is driving me crazy. Restart... no sound .... :(
Realtek again in alsamixer


Well looks like that I'm going to do a re-install of Ubuntu. If this does not fix it with the Realtek Onboard sound disabled in BIOS, I'm going back to window$ :(

---

### Post by ROUBOS on 2007-09-15
THIS IS DRIVING ME CRAZY.
I just did a shutdown, then boot and it works again.
Did a restart to double check, and it works. Don't know what's going on.

---


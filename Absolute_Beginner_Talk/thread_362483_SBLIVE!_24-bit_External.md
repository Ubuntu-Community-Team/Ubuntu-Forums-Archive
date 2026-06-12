---
title: "SBLIVE! 24-bit External"
date: 2007-02-15
forum: Absolute Beginner Talk
---

### Post by nevron on 2007-02-15
i have a problem with default soundcard settings under gnome in ubuntu 6.10 edgy
during the installation of my system i was using my onboard soundcard and later i bought an SBLIVE! 24-bit External soundcard which operates through usb

when i first log into ubuntu everything seems to work fine. applications like amarok and xmms tend to work for a while and then suddenly all sound applications fail to initliaze my soundcard. under the menu system>preferences>sound in the sound tab, it reads MPU-401 UART as the default sound device. i click on the dropdown box and switch to SBLIVE! 24 bit, it seems to switch to it but then when i go back and look at the setting it reads MPU-401 UART again for some reason UBUNTU refuses to use my SBLIVE! as the primary soundcard.

any help will be apreciated.
thanks in advance.

---

### Post by NewOldTimer on 2007-02-15
Try right clicking volume icon>open volume control>click file>change devise to SB Live 24bit External{alsa mixer}      see if that helps you out, I'm just now playing with mine trying to record thru it, will let you know if I find out anything interesting, let me know how it goes.

---

### Post by nevron on 2007-02-15
No luck here. In the preferences tab the 24 bit Live Alsa Mixer is already selected somehow Ubuntu tries to use my disabled onboard card i guess. Altough I have disabled it from the bios the system is still trying to use it as the default soundcard.
Do you have any additional controls under the volume control other than the PCM
There should be a mixer or something but all i get is a PCM control also there is a capture tab  but nothing else.
Is there a driver for the 24 bit live usb?

Thanks in advance.

---

### Post by NewOldTimer on 2007-02-15
nevron,   sorry your still having prob's..my external set up fine. once sb is your preference that's all the options it shows{PCM}, you can follow my above steps and select other choices and that puts all the controls back up, what I did was to make sure everything was enabled then switched device's back to SB and thenI saved the session and restared, worked for me, I'm using Edgy/gnome, all I can offer as I'm too new to start config/troublshooting just thought I'd offer what worked for me, surely some-one else will offer some insight.

Blind leading the Blind you see?

---

### Post by nevron on 2007-02-16
OldTimer thank you for your advices. I guess I will have to reinstall my Ubuntu in order to get it working correctly, because even though it is working right now, I still have the mpu-401 as the default soundcard. I think I am using my sblive for the output of the sound. Anyways I will try to install some sequencer software and try to run them through my sblive if they work I'll give up trying to set up my default soundcard as SBLIVE! 24-bit external. Or else I will have to reformat and install a fresh Ubuntu.

---

### Post by nevron on 2007-02-16
And I have a question are you able to run multiple sound applications at once like xmms and amarok togather? Do you get any errors? Did you try to run amarok and run some you tube videos at the same time? Do you get any errors while doing so? Thanks in advance.

---

### Post by NewOldTimer on 2007-02-16
nevron, sorry for the late reply{had to get some sleep}.  Yes I can run multiple apps, I don't use amarok, but I can use xmms and Mplayer together, also no problems with on-line video's and xmms at the same time... no error's here...did finally get SB and audacity  sinc'd too.
   I also don't have your problem of device choice not showing correctly, I'm really at a loss to offer any path for you to try.
  Afterthought... are you using optical out-put, I'm going from headphone jack out to my PA, I don't have an optical cable so don't know how or if that would cause anything related.

---

### Post by equilibrium on 2007-02-17
I have this soundcard also. I'm having a few problems getting OSS working and also certain apps :(
I tried the gentoo ALSA SBLive 24bit USB howto, but it doesn't seem any different. There's no /dev/dsp devices either :(

---


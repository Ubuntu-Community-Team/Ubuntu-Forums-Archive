---
title: "everything seems fine but the sound still doesn't come out?"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by telly0050 on 2007-04-28
it seems like many people have this problem, and i read through many dozens of posts and tried, but nth realy works.

my situation is:

when i open system->preferences->sound, i get "autodetect, via 82xx modem, via 8235, alsa advance linux..., esd enlighten sound daemon and oss open sound system" on 3 sound playback options. 

when i choose "autodectect" and 'esd enlighten..", click on "test", nothing happen;
when i choose "via 8235" and "oss open sound system" to test, i hear a "dooooooooo..." sound;
when i choose "via 82xx modem", "alsa",  i get "audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Resource busy or not available." this message;

for device, i have "via 8235(alsa mixer); via 82xx modem(alsa mixer); realtak alc101(oss mixer)
but no matter which one i choose, i still don't hear any sound from my speaker.

i have this problem since 6.06, today i updated to 7.04, it is still not fixed. 

and i tried the alsamixer command and turn all the things on, not working.

can someone please help (step by step, b/c im totally newbie at linux system)?
this problem annoy me for a long time.

thx m(_ _)m

---

### Post by Sef on 2007-04-28
Try this to get sound.   From the Terminal:

```
gksudo gedit /etc/modprobe.d/alsa-base
```

then change the 2 to 0.  Before:  > options snd-intel8x0m index=-2 to After > options snd-intel8x0m index=-0

From mine:

> # Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options cx88-alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-0
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2

---

### Post by telly0050 on 2007-04-28
> **Sef said:**
> Try this to get sound.   From the Terminal:

```
gksudo gedit /etc/modprobe.d/alsa-base
```

then change the 2 to 0.  Before:   to After 

From mine:

thx for the reply

i enter the command and i get this msg: (gedit:16064): 
GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

the file pop up anyways so i edit the change as u said (btw my file is exactly like yours) and save
but it still not working....

---

### Post by Sef on 2007-04-28
> enter the command and i get this msg: (gedit:16064):
GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

That always comes up.  Not sure why.  But never had any problems because of it.

> the file pop up anyways so i edit the change as u said (btw my file is exactly like yours) and save
but it still not working....


Did you reboot?  Sometimes you need to do that.  Also at times, I will boot up with no sound, so I just reboot, and the sound is there.

---

### Post by telly0050 on 2007-04-29
still not working
does anyone have other suggestion?

---

### Post by telly0050 on 2007-04-29
ok i changed some setting in the xserver and now im able to hear system sound
but when i open youtube, i still dont hear any sound, wut's the problem now?

---


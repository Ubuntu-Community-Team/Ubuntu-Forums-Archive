---
title: "24&quot; LED Cinema Display + GeForce 9400M graphics"
date: 2009-04-10
forum: Apple Hardware Users
---

### Post by hajk on 2009-04-10
I've been trying for over a week now to get decent screen resolution on my Apple 24-inch LED Cinema Display (ALCD) as run in GNU/Linux
on my new 2009 Mac Mini 3,1 with integrated GeForce 9400M graphics. The nVidia drivers don't yet work (I've tried up to the 180.29 version), 
the built-in Xorg "nv" driver doesn't work either, but the default "vesa" driver works in a fashion.

In a fashion, because VESA gives the following sort of messages in /var/log/Xorg.log.0```

(II) VESA(0): VESA VBE DDC read failed

(WW) VESA(0): Unable to estimate virtual size
```and then settles on a resolution much less than the 1920x1200 the 24" ALCD is capable of (Jaunty gets to 1280x800, Sid to 1600x1200). 
Clearly, VESA needs a little help here...

After some experimenting, I've found the following Sections in /etc/X11/xorg.conf sufficient to get VESA to display 1920x1200 at a conservative
refresh rate of 60Hz```

Section "Device"
        Identifier      "Configured Video Device"
        Driver          "vesa"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
        HorizSync       69.0 - 79.0
        VertRefresh     55.0 - 65.0
        Modeline        "1920x1200" 204.95 1920 2024 2272 2744 1200 1200 1203 1244
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        DefaultDepth    24
        SubSection "Display"
                ViewPort        0 0
                Virtual         1920 1200
                Modes           "1920x1200"
        EndSubSection
EndSection
```
The /var/log/Xorg.log.0 now shows that the built-in 1920x1200 mode (17d) has been recognized by VESA, and restarting Xorg confirms that this
resolution is now indeed in use. 

I'm sure there must be other Modelines that work, e.g. at 75Hz, but the present one will do for me until nVidia come through with some updated stuff. 
Needless to say that I'm not responsible for any damage to your ALCD if you try other Modelines or make a typo...;)

---

### Post by sowelie on 2009-04-10
When you say the latest nVidia drivers don't work what do you mean?  Do you get low graphics mode when you try to use them?

---

### Post by hajk on 2009-04-10
No, I mean exactly what I say, they don't work, as in not applicable, or Xorg not even starting.

Mind you, this is due to the combination of ALCD + Mini Display Port + GeForce 9400M; there is 
no problem with the nVidia drivers when using a Samsung LCD monitor via the miniDVI - DVI adapter.

---

### Post by cyberdork33 on 2009-04-10
DDC doesn't work over displayport yet?

---

### Post by hajk on 2009-04-10
Apparently DDC doesn't work with the Apple MDP.

BTW, I'm working with the 2.6.29-amd64 kernel in Sid right now -- applesmc and hid_apple modules recognize all hardware, BT alum small keyboard + mighty mouse work as BT devices, only problem so far is ALSA (model=imac24 no longer works in Sid, it did in Lenny and in Jaunty Beta). I'm working on a complete setup report, so we can hit the ground running with the successor to Jaunty.

---

### Post by cyberdork33 on 2009-04-10
> **hajk said:**
> only problem so far is ALSA (model=imac24 no longer works in Sid, it did in Lenny and in Jaunty Beta). I'm working on a complete setup report, so we can hit the ground running with the successor to Jaunty.
i think people were using mbp3 for iMacs and that was working too. might try that.

---

### Post by hajk on 2009-04-11
ALSA now works via the speakers on the ALCD! No model specification is necessary for the snd_hda_intel module with the 2.6.29 kernel,
"imac24" works in Jaunty Beta for the 2.6.28 kernel, but stops sound dead in its tracks with 2.6.29.

The volume controls (F10,11,12) work out-of-the-box on the sliders called "Speaker" in Volume Control (Apple USB audio device). 
Alsamixer shows this too.:guitar:

Recording and mixing (with Audacity, e.g.) will likely work via the alternative HDA NVidia audio device, as its Preferences allow making
various Input visible in Volume Control.

---

### Post by cyberdork33 on 2009-04-11
> **hajk said:**
> alsa now works via the speakers on the alcd! No model specification is necessary for the snd_hda_intel module with the 2.6.29 kernel,
"imac24" works in jaunty beta for the 2.6.28 kernel, but stops sound dead in its tracks with 2.6.29.

The volume controls (f10,11,12) work out-of-the-box on the sliders called "speaker" in volume control (apple usb audio device). 
Alsamixer shows this too.:guitar:

Recording and mixing (with audacity, e.g.) will likely work via the alternative hda nvidia audio device, as its preferences allow making
various input visible in volume control.
alcd?

---

### Post by stream303 on 2009-04-12
My foss "nv" driver stopped working well with the latest xorg releases and I had to bypass hal and create a custom modeline in xorg to get it to work.

I'm running a 22" widescreen at 1680x1050 at 70hz and here's how I generated the modeline

```
gtf 1680 1050 70
```

Put the resultant modeline into the "Monitor" section xorg.conf.  Mine looks like this:

```
Section "Monitor"
	Identifier	"Configured Monitor"
	HorizSync	30-82
	VertRefresh	50-75
	Option		"DPMS"
	**Modeline	"1680x1050_70" 173.83 1680 1792 1976 2272 1050 1051 1054 1093 -HSync +Vsync**
EndSection
```

(Be aware of the + / - sync values and don't inadvertently swap + or -)

Normally I had no problem just modifying the typical "modes" section of xorg.conf for my resolution, but lately it seems I have to take these custom generated modelines to bypass hal to convince the nv driver that it was ok. :)

Mind you, this was on an arch-linux amd64 box, but thought I'd throw this out just in case...

---

### Post by hajk on 2009-05-07
Well, it certainly is food for thought (although not entirely sure how this relates to the Apple Led Cinema Display).

**@cyberdork** ALCD = _A_pple _L_ed _C_inema _D_isplay, got it now?:)

---

### Post by cyberdork33 on 2009-05-07
> **hajk said:**
> **@cyberdork** ALCD = _A_pple _L_ed _C_inema _D_isplay, got it now?:)hehe... I thought you were referring to some weird software or port or something.

---

### Post by hajk on 2009-05-07
Yeah, now that I've gotten your attention... just want to report that there isn't any change yet in using the ALCD thru the MDP (mini display port): the latest nvidia still doesn't work (scrambles the screen), DDC is not working in Xorg, but the VESA work-around in my OP works OK. It just takes time for these things to work their way thru either the nvidia source or Xorg, or both.

I mentioned elsewhere that there is no problem running an LCD through the mini-DVI port of my MacMini. 

Edit: ...and, judging by the Apple Support Forums, neither is there a problem running Windows Vista on the ALCD thru the MDP in a Boot Camp partition.

---


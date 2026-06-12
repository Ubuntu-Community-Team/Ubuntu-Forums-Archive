---
title: "radeon 9000 issues on MATE 14.04"
date: 2015-05-20
forum: Apple Hardware Users
---

### Post by rican-linux on 2015-05-20
So I replaced a bad HD on my PowerMac G4 with a SSD from OWC. I wanted to install Ubuntu-MATE 14.04 on it. However I am running into serious graphics issues. When I use the following parameters I get the screen with all the colors off.

```
radeon.modeset=1
radeon.modeset=1 radeon.agpmode=-1
radeon.modeset=1 video=offb:off radeon.agpmode=-1
```

when I these however I desktop comes up clean but freezes

```
radeon.modeset=1 video=offb:off video=radeonfb:off radeon.agpmode=-1
```

This is the first time those parameters failed me. Anyone ran into similar issues?

---

### Post by luigiburdo on 2015-05-23
rican i have the same issue with 7800gtx on quad g5 ... i think is the xorg

---

### Post by este.el.paz on 2015-05-23
> **luigiburdo said:**
> rican i have the same issue with 7800gtx on quad g5 ... i think is the xorg

I would agree . . . with 14.04 I had to "configure xorg.conf" . . . you should be able to find the directions in the FAQ, have to "service stop lightdm" . . . then I think I jumped into a TTY to run the rest of the commands . . . to "mv" the xorg.conf to etc/X11/xorg.conf . . . pretty straightforward . . . more or less fixed the graphics issues . . . .  15.04 seems to be a different story.

If u can't find the simple details I might have it in an email somewhere posted in Lu Users list . . . or something.

e..

---

### Post by rican-linux on 2015-05-23
Is it just with this card? 9600 and 9700 cards I can get KMS working with those boot parameters

---

### Post by rican-linux on 2015-05-23
I created my xorg.conf moved it to /etc/X11 and still KMS freezes when enabled with *radeon.agpmode=-1*. That option was suppose to stop freezes.

---

### Post by este.el.paz on 2015-05-24
> **rican-linux said:**
> I created my xorg.conf moved it to /etc/X11 and still KMS freezes when enabled with *radeon.agpmode=-1*. That option was suppose to stop freezes.

@r-l:

Exceeding my skill level on the 9000 card question, the "configure" process should have "seen" that card and handled it . . . but the xorg deal has historically "fixed" the freezing problem . . . along with the boot params . . . which you could add to Yaboot.conf . . . .  Try a few "apt-get update/upgrades"???? sometimes that provides new stuff based upon your changes, etc??

e..

---

### Post by rican-linux on 2015-05-25
Yeah I am thinking that this radeon 9000 pro card is just not going to work. I am looking at getting a radeon 9800 pro card.

---

### Post by dand1972 on 2015-05-27
I've had the same problems with the 9000 Pro in a Sawtooth.  Looks like KMS and Power Macs with 9000s don't play well together.

---

### Post by rican-linux on 2015-05-27
Good to know i am not alone

---

### Post by rican-linux on 2015-06-04
I got KMS working, but I need to enable "NoAccel" in Xorg. So I still do not have HW aceleration.

```
Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        Option     "NoAccel"                   "True"	
        #Option     "SWcursor"           	# [<bool>]
        Option     "EnablePageFlip"            "True"	
        Option     "ColorTiling"               "True"	
        Option     "ColorTiling2D"             "True"	
        Option     "RenderAccel"               "True"	
        #Option     "SubPixelOrder"      	# [<str>]
        Option     "AccelMethod"               "XAA"	
        #Option     "EXAVSync"           	# [<bool>]
        #Option     "EXAPixmaps"         	# [<bool>]
        #Option     "ZaphodHeads"        	# <str>
        Option     "EnablePageFlip"            "True"	
        #Option     "SwapbuffersWait"    	# [<bool>]
	Identifier  "Card0"
	Driver      "radeon"
	BusID       "PCI:0:16:0"
EndSection
```

---


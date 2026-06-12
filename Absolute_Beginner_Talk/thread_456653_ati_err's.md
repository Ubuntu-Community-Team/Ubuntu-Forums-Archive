---
title: "ati err's"
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by silent1643 on 2007-05-27
still trying to get my ati x850 series card to do desktop effects. I have used envy every time it has been updated and still no go. Here is a screen shot of what my desktop looks like with restarting my session in xgl

[[IMG]http://img166.imageshack.us/img166/9439/screenshotju3.th.png[/IMG]](http://img166.imageshack.us/my.php?image=screenshotju3.png)

any help would be great :D

---

### Post by silent1643 on 2007-05-28
bump

---

### Post by freefromXP on 2007-05-28
This may help I used this to get my 9800pro working.  Fixed all my desktop and gaming issues.  UT2004 plays great and Beryl rocks.  Hope it helps.

[http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon]("http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon")

---

### Post by silent1643 on 2007-05-28
> **freefromXP said:**
> This may help I used this to get my 9800pro working.  Fixed all my desktop and gaming issues.  UT2004 plays great and Beryl rocks.  Hope it helps.

[http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon]("http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon")

thanks, on the bottom of page one where it says my direct rendering should be set to yes, mine is set to no for some reason? i did restart my x session but am i suppose to change my session to xgl?
```
direct rendering: No

```

---

### Post by overdrank on 2007-05-28
> **silent1643 said:**
> thanks, on the bottom of page one where it says my direct rendering should be set to yes, mine is set to no for some reason? i did restart my x session but am i suppose to change my session to xgl?
```
direct rendering: No

```

Hi if I am correct ( oh I really hope I am ) you don't get direct rendering with xgl. Well that is what I get with my xgl and beryl. :KS

---

### Post by silent1643 on 2007-05-28
> **overdrank said:**
> Hi if I am correct ( oh I really hope I am ) you don't get direct rendering with xgl. Well that is what I get with my xgl and beryl. :KS

hm.. i hate this, why can't my card just work lol

here is some code from my  xorg.conf

```
Section "Device"
	Identifier	"ATI Technologies Inc R481 [Radeon X850XT-PE]"
	Driver                "radeon"
        BusID                "PCI:1:0:0"
        Option          "XAANoOffscreenPixmaps"
        Option "AGPMode" "4"
        Option "AGPFastWrite" "true"
        Option "DisableGLXRootClipping" "true"
        Option "AddARGBGLXVisuals" "true"
        Option "AllowGLXWithComposite" "true"
        Option "EnablePageFlip" "true"
EndSection
```

```

Section "ServerLayout"
        Option          "AIGLX"         "true"
	Identifier	"Default Layout"
  	screen 		"Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"stylus"	"SendCoreEvents"
	Inputdevice	"cursor"	"SendCoreEvents"
	Inputdevice	"eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
	Option		"Composite"	"Enable"
EndSection

```

and my glxinfo

```
server glx vendor string: SGI
client glx vendor string: SGI
OpenGL vendor string: Mesa project: www.mesa3d.org

```

---

### Post by overdrank on 2007-05-28
> **silent1643 said:**
> hm.. i hate this, why can't my card just work lol

OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
[/code]

Well I really know how you feel and I feel just as bad. I guess I will have to install feisty just so I can know how to do this. Really sorry but I can't help with feisty. :(

---

### Post by silent1643 on 2007-05-28
> **overdrank said:**
> Well I really know how you feel and I feel just as bad. I guess I will have to install feisty just so I can know how to do this. Really sorry but I can't help with feisty. :(

kill me now](*,)

---

### Post by overdrank on 2007-05-28
> **silent1643 said:**
> kill me now](*,)

Come on some help for the poor  user's!:(

---


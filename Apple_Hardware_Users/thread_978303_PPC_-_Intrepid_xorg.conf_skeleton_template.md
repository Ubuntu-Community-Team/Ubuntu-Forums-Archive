---
title: "PPC - Intrepid xorg.conf skeleton template"
date: 2008-11-11
forum: Apple Hardware Users
---

### Post by stream303 on 2008-11-11
For some late-model Macs, Intrepid might not pose any problems - for others you may have to go back with rescue mode, and manually edit /etc/X11/xorg.conf for your video.

After booting with Intrepid, you may be shocked to find that xorg.conf contains nothing at all.  To top it off, just copying over an old xorg.conf sometimes results in some weirdness, now that mice and other inputs are handled differently.  I'm still studying up on the changes.

Here is a template that can help.  This is what I am running on my G5 iMac, so change your horizontal and video frequencies, driver, etc to match the needs of your model.

(I did not need to configure my xorg.conf on my box, until I wanted FPDithering, so decided to pursue this a little more...)

```

# THIS IS FOR MY 20" G5 iMAC - change accordingly!
# FPDithering is only for nv driver and lcd screens

Section "Monitor"
	Identifier	"Configured Monitor"
        HorizSync       28-84
        VertRefresh     43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
 	SubSection      "Display"
       		Depth   24
       		Modes   "1680x1050"
       	EndSubSection
EndSection

Section "Module"
        Disable "glx"
        Disable "dri"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nv"
	Option	"FPDither" "true"
EndSection
```

So there you go - for you intrepid souls that want to put 8.10 on a machine that doesn't come right up with video.   This should help as long as you change the video freqs, driver (ati, nv, radeon, r128) etc per the faqs and threads.)  I had to use a similar file for my X86/64 desktop to get past 800x600...

Note: a common mistake is to put "quotes" around the bit depths and vertical and horizontal sync rates.

---

### Post by lemonbar on 2008-11-11
:guitar:

This has been driving me CRAZY!!!!!  I could get Edgy to work fine, mostly (software update didn't work - that was kind of a drag...), but I think this might be the answer to my problem...

Thank you!

---

### Post by stream303 on 2008-11-18
Guess what works now?  I can now activate FPDithering with a very small /etc/X11/xorg.conf with only one section, without Intrepid dropping me into low-graphics mode as punishment for doubting it. :)

ack, I hate when something just "starts working".  Check it out, this is all I have now to enable dithering:

```
Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nv"
	Option	"FPDither" "true"
EndSection
```

---

### Post by pxwpxw on 2008-11-19
The same sort of mini xorg.conf working here, intrepid xubuntu(for a MacBook using fbdev).

/etc/X11/xorg.conf

```

Section "Device"
	Identifier	"Configured Video Device"
	Driver 		"fbdev"
EndSection

```
It seems you can just provide an xorg.conf with only a valid Section with the particular stuff you want, restart X and it goes.
(Or I can still get a template by runnung dpkg-reconfigure xserver-xorg).

---

### Post by stream303 on 2008-11-19
> **pxwpxw said:**
> (Or I can still get a template by runnung dpkg-reconfigure xserver-xorg).

Whoa!  Great tip for Intrepid users especially!  So even though or old friend dpkg-reconfigure xserver-xorg got deprecated in what - Hardy I think, at least it serves as an xorg.conf template creator!

Nice one....

---

### Post by milkwood on 2008-12-08
[http://www.cyberciti.biz/faq/howto-use-linux-ddcprobe-command/](http://www.cyberciti.biz/faq/howto-use-linux-ddcprobe-command/)

I've thought this problem might be caused by defining of HorizSync and VertRefresh.
We should know proper values to fit on each computers.
If you have this problem,try this above.

---

### Post by stream303 on 2008-12-08
ddcprobe is good stuff - although sometimes the ppc hardware doesn't respond to it during installation, forcing us to manually edit our configs.

Doesn't hurt to try however!

---

### Post by milkwood on 2008-12-09
I'm sorry,I didn't mean to hurt to try or try to hurt either.
I thought if you got low graphic rescue problem after install intrepid,this might be work.
My thought is very simple.
Firstly,I didn't know my proper values of horizsync and vertrefresh.
Then I found a way how to know my proper values.
Secondly,I thought some people might not know that as well as me.
If only you rewrite proper values of the two,I think,It might be gonna be all right.
That's all.
It's very simple.

By the way,I tried to ddcprobe and edited xorg.conf according to the result.
There is absolutely no problem.
I'm on hardy though.
In fact,if this horiz and vert thing doesn't work,I have no idea to alter this.

---


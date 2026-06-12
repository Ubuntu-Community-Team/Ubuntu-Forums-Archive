---
title: "Graphics driver installed, but appears to be not working. o.O GNOME works fine though"
date: 2007-06-29
forum: Absolute Beginner Talk
---

### Post by Bensky on 2007-06-29
EDIT: Wow, I'm an idiot. I didn't even need to install any graphics card drivers like "fglrx." I restored my backup of xorg.conf and guess what, glxgears ran at 2500+ FPS with no errors.











Okay, so I finally got ubuntu working and proceeded to install my graphics card driver after downloading all 72 software updates. :D

I used Envy, which seemed to work fine with my ATI Radeon 9600 XT. It downloaded the drivers, installed them, and restarted my computer. However, I noticed something strange: When I got to GRUB, there were now more boot options than before. Before, I just had Ubuntu, Ubuntu recovery mode, and Windows XP Pro. Now, I seem to have 2 different kernel versions - a newer one and one that seems to be slightly older. I believe the 2 versions were: 2.6.21.6 and 2.6.21.5...I think that Envy put the 2.6.21.5 version. I didn't know why it did this, so I just booted into the one with the higher version number.

Everything appears to be installed correctly: If I go to applications > accessories I see a "Catalyst Control Center" which is the right control center for my graphics card.

To test if it was installed properly, I ran "glxgears" in terminal, but for some reason my FPS was only about 300 each time...I read somewhere if the graphics card driver is installed correctly you should get like 1000+ FPS. Also, when I run glxgears I get an error message on the first line, but it runs anyway:
```

Xlib:  extension "XFree86-DRI" missing on display ":0.0".

```

=====================================
Here is the graphics card part of my xorg.conf:
```

Section "Device"
	Identifier	"ATI Technologies Inc RV350 AR [Radeon 9600]"
	Driver	"fglrx"
	Option	"VideoOverlay" "on"
	Option	"OpenGLOverlay" "off"
	BusID		"PCI:1:0:0"
EndSection

```

If anyone can help with this, that would be nice. :P

---

### Post by Bensky on 2007-06-29
bump. :(

---

### Post by overdrank on 2007-06-29
> **Bensky said:**
> Okay, so I finally got ubuntu working and proceeded to install my graphics card driver after downloading all 72 software updates. :D

I used Envy, which seemed to work fine with my ATI Radeon 9600 XT. It downloaded the drivers, installed them, and restarted my computer. However, I noticed something strange: When I got to GRUB, there were now more boot options than before. Before, I just had Ubuntu, Ubuntu recovery mode, and Windows XP Pro. Now, I seem to have 2 different kernel versions - a newer one and one that seems to be slightly older. I believe the 2 versions were: 2.6.21.6 and 2.6.21.5...I think that Envy put the 2.6.21.5 version. I didn't know why it did this, so I just booted into the one with the higher version number.

Everything appears to be installed correctly: If I go to applications > accessories I see a "Catalyst Control Center" which is the right control center for my graphics card.

To test if it was installed properly, I ran "glxgears" in terminal, but for some reason my FPS was only about 300 each time...I read somewhere if the graphics card driver is installed correctly you should get like 1000+ FPS. Also, when I run glxgears I get an error message on the first line, but it runs anyway:
```

Xlib:  extension "XFree86-DRI" missing on display ":0.0".

```

=====================================
Here is the graphics card part of my xorg.conf:
```

Section "Device"
	Identifier	"ATI Technologies Inc RV350 AR [Radeon 9600]"
	Driver	"fglrx"
	Option	"VideoOverlay" "on"
	Option	"OpenGLOverlay" "off"
	BusID		"PCI:1:0:0"
EndSection

```

If anyone can help with this, that would be nice. :P

HI Ok first the kernels, you do have a extra not because of envy but because of the updates. I would advise to keep the additional kernel because if something happens to your current kernel you may use the other kernel to save data. 
Now for the ati card. I personally like ATI and also Nvidia, the ati card can use different drivers and if you are not happy with the driver install you may try the restricted driver. It can be found under system, administration, restricted driver. If it is not there then you can research and choose which driver you wish to try, I personally like the xgl for the effects I can achieve with Beryl and desktop effects.
So I hoped this helps in some way and good Luck! :D

---

### Post by Bensky on 2007-06-29
> **overdrank said:**
> HI Ok first the kernels, you do have a extra not because of envy but because of the updates. I would advise to keep the additional kernel because if something happens to your current kernel you may use the other kernel to save data. 
Now for the ati card. I personally like ATI and also Nvidia, the ati card can use different drivers and if you are not happy with the driver install you may try the restricted driver. It can be found under system, administration, restricted driver. If it is not there then you can research and choose which driver you wish to try, I personally like the xgl for the effects I can achieve with Beryl and desktop effects.
So I hoped this helps in some way and good Luck! :D

Erm. I already have fglrx installed, but it appears not to be working. See my post above, but thanks for explaining about the kernels...;)

---

### Post by Bensky on 2007-06-30
Anyone else? Sorry if I seem impatient. :(

---

### Post by overdrank on 2007-06-30
[QUOTE=Bensky;2937482]EDIT: Wow, I'm an idiot. I didn't even need to install any graphics card drivers like "fglrx." I restored my backup of xorg.conf and guess what, glxgears ran at 2500+ FPS with no errors.
/QUOTE]

Great glad to hear if I may ask which driver is your back up using now. I have a x300 on my desktop and works great with the ati driver which was installed at the beginning.

---


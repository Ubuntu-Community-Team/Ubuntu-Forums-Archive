---
title: "Why the resolution on my login screen is low?"
date: 2007-07-26
forum: Absolute Beginner Talk
---

### Post by wasim2050 on 2007-07-26
When I installed Ubuntu 7.04 I was using i810 driver for my 845g Intel graphic card and therefore I was getting only 1024x768 resolution on both my login screen as well as on my desktop but I was not satisfied because on Windows XP I was used to working in a 1152x864 resolution environment. So I updated my driver from i810 to intel and then I was able to see 1152x864 resolution on my desktop but on my login screen I am getting a low resolution of only 800x600.

So does anybody knows how to get 1152x864 resolution on both the login screen as well as on desktop.

---

### Post by Tecguy2 on 2007-07-26
i have never encounted that before but i have a nvidia geforce 7600 
does the res change at all on the login sreen when you change to other res's

---

### Post by wasim2050 on 2007-07-26
When I start the system I get a login screen of 800x600 res. and as soon as I login the resolution changes automatically to 1150x868 then if I choose to logout so that I can login again at this time the login screen is at high resolution. So I see low resolution at the login screen only when system starts or restart.

---

### Post by wasim2050 on 2007-07-26
Can nobody can help me with this problem.

---

### Post by wasim2050 on 2007-07-27
Still no reply :confused:

---

### Post by anewguy on 2007-07-27
I checked gdmsetup, since it will update the custom gdm configuration file.  I could find nothing there for specifying the resolution of the logon screen.  I suspect somewhere in gdm configuration stuff there must be something that sets this.  I'll keep looking and see if I can find anything.:)

---

### Post by mcduck on 2007-07-27
Try removing all other resolutions from xorg.conf. After that GDM should have no other options than using te resolution you want ;)

---

### Post by wasim2050 on 2007-07-27
Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel 845G"
	Monitor		"Sync Master"
	DefaultDepth	24
	SubSection "Display"
	Depth		24
	Modes		"1152x864"
	EndSubSection
EndSection


I try removing all the resolution as u said but still the login screen is coming in low resolution and when I check System>Preferences>Screen Resolution I can see all the resolution inspite of leaving only one resolution in xorg.conf

---

### Post by wasim2050 on 2007-07-28
I think my problem is unique:mad:

---

### Post by jingo811 on 2007-07-28
Don't know if this fix applies to you but for ppl who don't get proper resolutions at all they do this command in terminal.

> sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by wasim2050 on 2007-07-29
Nope the problem remains.

---

### Post by az on 2007-07-29
> **wasim2050 said:**
> Nope the problem remains.


How much ram does your video card have?

Try booting into recovery mode and running

dpkg-reconfigure -plow xserver-xorg

answer the questions.  take the default when you are not sure.  When you get to the color depth and resolution, Try picking 16-bit instead of 24 bit. and dissable 800x600.

when it finishes up, run

init 2

---

### Post by wasim2050 on 2007-07-30
Its not working.

The resolution of the login screen is still low.

---

### Post by mcduck on 2007-07-30
You could try adding 'vga=792" to your kenrel boot options in /boot/grub/menu.lst to make Ubuntu boot using 1024x768 resolution. This should also change the GDM resolution.

---

### Post by Naci Sey on 2007-07-30
I've been having a similar problem re lack of options for setting the screen resolution of my LG Flatron monitor. The Screen Resolution window shows only three options, the highest being 1024 x 768. I did look at the xorg.conf file but don't know what to do with it - what to add or delete.

---


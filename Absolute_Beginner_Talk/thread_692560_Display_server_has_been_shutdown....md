---
title: "Display server has been shutdown...?"
date: 2008-02-09
forum: Absolute Beginner Talk
---

### Post by StarThorn1 on 2008-02-09
I try to start ubuntu from the cd. I get the message: The display server has been shutdown about 6 times in the last 90 seconds. It is likley that somthing bad is going on. Waiting 2 minutes before trying display 0.

After this is keep getting the same message. What am I doing wrong and how do I fix it?

---

### Post by StarThorn1 on 2008-02-09
please help

---

### Post by spiderbatdad on 2008-02-09
possibly a display setting in your bios can be set to pci and analog vga

---

### Post by carlinuxlearner on 2008-02-09
Ubuntu is having trouble recognizing your graphics card, you can try starting it in "Safe Graphics mode" and see if that works, if not I can give you instructions on making it work.

C@RL

---

### Post by StarThorn1 on 2008-02-11
I tryed safe mode one but it gave me the same problem. My GPU is ATI   x 1600

---

### Post by carlinuxlearner on 2008-02-11
Well you can try this.
Once it's booted and is giving you that message, press CTRL+ALT+F1 and type in "vim /etc/X11/xorg.conf" (make sure you type in EXACTLY what I just told you too) once your in "Vim" scroll down (with the Pagedown key) and fine that part that says "Device" (it will look something like this)

Section "Device"
	Identifier	"nVidia Corporation NVIDIA Default Card"
	Driver		"nvidia"
	Busid		"PCI:0:18:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

hit the "I" key (the eye key, in case you couldn't tell) and change the part that says 

"nvidia"

(or it might be "nv") 

to "vesa", then press ESC and next press SHIFT+: (thta's the SHIFT key and the Semicolon key) and type "wq" then enter, it should save and exit.
now type in your terminal "startx"
and I think it should work.

C@RL

---

### Post by StarThorn1 on 2008-02-12
wouldnt you know it...My hard drive died on me at 5am this morning.  I'm going to have to wait for the weekend before I can get my old 200 GB HD so I can try what you said.

PS for the record im duel booting vista and Linux

---

### Post by Thraxarious on 2008-03-10
I happen to be having the same problem. It just cannot start the display server. I checked my xorg.conf file and it already is showing the VESA driver.

The strange part is, I had this booted and installed earlier, but installed all the current updates and things went whacko. 

This is not new, I have tried installing from CD before on this laptop and it did the very same thing.

I am using the ATI Mobile Radeon 1600 just like the above poster.

---

### Post by carlinuxlearner on 2008-07-12
ATi's drivers are notorious on Linux.

C@RL

---


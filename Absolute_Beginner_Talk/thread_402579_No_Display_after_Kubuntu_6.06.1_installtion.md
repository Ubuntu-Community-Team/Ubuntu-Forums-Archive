---
title: "No Display after Kubuntu 6.06.1 installtion"
date: 2007-04-05
forum: Absolute Beginner Talk
---

### Post by hec1979 on 2007-04-05
I know this is a common problem here in the forums but I have found no info to help me. I just finished installing kubuntu and it will not boot correctly because of the resolution. 

This was also true when using the live CD it would only work when i manually chose 640x480x16 or 640x480x32 when selecting it using the VGA option.

How can I configure it so that will always choose 640x480x16 when it initially boots up. Below is the following information for video

Intel Corporation 82830 CGC Chipset Controller using the i810 driver

Hope you guys can help,

Hec1979****

---

### Post by crispy_420 on 2007-04-05
Couldn't you just get rid of the options you don't need in your xorg?

Is it just me or do a lot of people have issues with that Intel chipset?

---

### Post by hec1979 on 2007-04-05
I am really not familiar with the /etc/X11/xorg.conf file can you offer any suggestions on what I can do.  I tried to modify one of the resolution parameters to 640x480 but it was no help I even tried to add it at the end of the boot entry in the /boot/grub/menu.lst like I saw in another thread, but that did not work either?

---

### Post by crispy_420 on 2007-04-06
This is just a guess, and I would like someone else to chime in on this too, but I would go about this by modifing the xorg. Get another opinion before you do this first as I'm just assuming.

sudo gedit /etc/X11/xorg.conf

put in admin password

comment out any option you don't need  (that is adding a # in front of the line that way you have an easy way to correct if failure)

change the DefaultDepth from 24 to 16

If it does not work (as in no GUI), you can edit via command line with this command:

sudo nano /etc/X11/xorg.conf

---

### Post by hec1979 on 2007-04-06
I tried to comment everything out and set the default depth to 16 but that did not work either.  Is there anyone who knows how to change the default boot resolution to 640x480x16 or 640x480x32 I am sure after this is accomplished I will be able to login into my new installation

---

### Post by crispy_420 on 2007-04-06
This is brand new install right? If so you have nothing to loss by doing this:

your default xorg is something like this:

> Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. Radeon R350 NH [Radeon 9800 Pro]"
	Monitor    "SyncMaster"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

May not be exactly yours. But try changing like so:

> Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. Radeon R350 NH [Radeon 9800 Pro]"
	Monitor    "SyncMaster"
	DefaultDepth     16
	SubSection "Display"
		Depth     16
		Modes    "640x480"
	EndSubSection
EndSection


Nothing to lose right? If I am way off, someone let me know.

---

### Post by hec1979 on 2007-04-06
Thanks for your help crispy_420 , but I was able to solve the problem by myself the soution is posted below.

All I had to do was at the following line to the end of the boot entry in the /boot/grub/menu.lst
as shown below. This will force it to boot at the proper resolution

vga=784[COLOR="Red"][/COLOR]
 
title    Ubuntu, kernel 2.6.15-26-386
root   (hd0,1)
kernel /boot/vmlinuz-2.6.15-26-386 root=/dev/hda2 ro quiet splash [COLOR="Red"]**vga=784**[/COLOR]
initrd  /boot/initrd.img-2.6.15-26-386

Below is a list that you may find useful if you run into the same problem and want to adjust the resolution to meet your computer screen needs

# Normal VGA console
# vga = normal
# VESA framebuffer console @ 1024x768x64k
# vga=791
# VESA framebuffer console @ 1024x768x32k
# vga=790
# VESA framebuffer console @ 1024x768x256
# vga=773
# VESA framebuffer console @ 800x600x64k
# vga=788
# VESA framebuffer console @ 800x600x32k
# vga=787
# VESA framebuffer console @ 800x600x256
# vga=771
# VESA framebuffer console @ 640x480x64k
# vga=785
# VESA framebuffer console @ 640x480x32k
# vga=784
# VESA framebuffer console @ 640x480x256
# vga=769

---

### Post by crispy_420 on 2007-04-06
Glad to see you solved an issue.

---


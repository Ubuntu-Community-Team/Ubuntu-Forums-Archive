---
title: "changing nv to nvidia in the xorg.conf"
date: 2006-09-22
forum: Absolute Beginner Talk
---

### Post by gogogo111 on 2006-09-22
Hello ubuntu forums, I finnaly switched to ubuntu today, and I wanted to get the nvidia drivers installed. I have a 6600GT. I installed easyubuntu and installed the nvidia drivers, but then it said to go to /etc/X11/xorg.conf and change nv to nvidia. I go there, change nv to nvidia, go to save, but I only see save as.

I click that, and i try to replace the current xorg.conf file, but it says I dont have permission to do that. 

Could anyone be kind enough to help me with this? Thanks!! :p

---

### Post by bulldog on 2006-09-22
You should use 

gksudo gedit /etc/X11/xorg.conf

gksudo gives you root rights to change that file.

When you get an error in terminal,don't pay attention to it,it's a known bug and cpmpletely harmless.

But you should use gksudo when you open an app. with a graphical interface [GUI].
Otherwise you use sudo voor root.

---

### Post by kpkeerthi on 2006-09-22
(deleted by the poster as it was already answered :)

---

### Post by Fully216 on 2006-09-22
You have to be superuser to edit this file.  Type is command and then edit you xorg.conf file:

sudo gedit /etc/X11/xorg.conf &

Then you should have no trouble saving.  :cool:

---

### Post by gogogo111 on 2006-09-22
> **Fully216 said:**
> You have to be superuser to edit this file.  Type is command and then edit you xorg.conf file:

sudo gedit /etc/X11/xorg.conf &

Then you should have no trouble saving.  :cool:


thanks! I just changed it, and saved it. Now do I restart? It didnt bring up anything telling me what just happened or anything. So how do I know if I was succesful? I want my old resolution back (Been running at 1024x768, my moniters res is 1440x900 ((widescreen 16:10))). will that be a problem?[-o<

---

### Post by kpkeerthi on 2006-09-22
Try ctr+alt+<backspace> to just restart xorg. better yet restart your machine.

---

### Post by tideline on 2006-09-22
You have to be superuser to edit that file.  So, the easiest way to do that, for me - and you if you know a little vi, is to open a shell and do:

To open a shell go to Applications -> Accessories -> Terminal.  In that term type:

*sudo vi /etc/X11/xorg.conf*

When it asks you for a password, use your user's password.

Find the entry for nv - which you tried to change earlier.  You will have to use ther arrows on you keyboard.

put the cursor on the n of nv.  Hit the x key, until the nv is gone.  Hit thE i key, and type nvidia.

Hit the ESC key once then :wq.  This will write the file and quit vi.

You will need to reboot after that.

PM me if you have any other question or need help.  There is probably a easier way to do this with gedit, but this is the way I would do it.

Mike

---

### Post by gogogo111 on 2006-09-22
K, just did that. But i still cant change my res to 1440x900. Any help?

 This was to kpkeerthi

---

### Post by kpkeerthi on 2006-09-22
[http://doc.gwos.org/index.php/ChangeResolution](http://doc.gwos.org/index.php/ChangeResolution) might help. There are couple of links at the bottom of the page that might interest you. (Yay! my 200th post)

---

### Post by tuxcantfly on 2006-09-22
sudo dpkg-reconfigure xserver-xorg

when the monitor section comes up, select the resolution you want

---

### Post by fragos on 2006-09-22
This will work but it will also change the driver back to "nv".  You'll need to "sudo gedit /etc/X11/xorg.conf" and change "nv" to "nvidia".  As an example, here's my Driver section.  Your Identifier will match your video card.

Section "Device"
	Identifier	"NVIDIA Corporation NV34 [GeForce FX 5200]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
EndSection

---

### Post by bodhi.zazen on 2006-09-23
> **kpkeerthi said:**
> Try ctr+alt+<backspace> to just restart xorg. better yet restart your machine.

> **tideline said:**
> ....  You will need to reboot after that.

Errr... [color=red]NO NEED TO REBOOT![/color] Just re-start X with the 3 finger salute
Crtl-Alt-Backspace.

gogogo111 if you are still having problems:

Monitor ? Post xorg.conf.

---

### Post by bodhi.zazen on 2006-09-23
> **tuxcantfly said:**
> sudo dpkg-reconfigure xserver-xorg

when the monitor section comes up, select the resolution you want

You should advise:```
sudo dpkg-reconfigure -phigh xserver-xorg
```

-phigh skips (uses default) all settings except resolution.

---


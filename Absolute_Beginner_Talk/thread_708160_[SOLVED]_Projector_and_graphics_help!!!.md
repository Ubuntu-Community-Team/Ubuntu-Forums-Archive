---
title: "[SOLVED] Projector and graphics help!!!"
date: 2008-02-26
forum: Absolute Beginner Talk
---

### Post by MikeSz on 2008-02-26
Im doing a presentation this morning and wanted to use my laptop to connect to a projector - its a Fujitsu Siemens Amilo PA 1510, using an ATI Radeon (of sorts).  fn+f4 should give me the projector but when I press it nothing happens!  I tried to set up a second screen, just as a standard 800x600 plug and play devicde (not seeing anything else that looked like it would work from the options) now, not only can I still not get a projector working, it seems to have screwed my graphics up - everything's large and its stopped using the ATI driver.  At its present location, it isnt connected to the internet - can anyone help with this please???

---

### Post by MikeSz on 2008-02-26
Ok, little update - ive now got the projector working (dont know how), ive reinstalled the Ati drivers, the only problem now is that my laptop screen is scrolling (i.e. I cannot see the whole screen, I have to move the mouse to the side and scroll the screen) however the projector is showing the screen perfectly!  I dont want to remove the projector in case I lose it again!  Anyone have any ideas that will get my laptop screen back to normal whilst retaining the projector

---

### Post by oedha on 2008-02-26
open terminal, then type :==> sudo dpkg-reconfigure -phigh xserver-xorg
what happen ?

---

### Post by MikeSz on 2008-02-26
I just tried that, though without the '==>' thingys, just started with sudo.  Screen went black and and stayed that way for aboutr 5 minutes before I re-booted.  Ive noticed that the projector will only work if its plugged in on boot.  If I disconnect the projector and re-boot, my screen returns to an almost normal size (i.e. everything is still large, but I dont have to scroll any more) though when I plug the projector in, I have to start scrolling again.  So I think the projector is forcing my laptop to accept 1024x768 as the projector screen displays perfectly.

My login screen is still huge though, and the font is also massive. im used to 1200x800 and everything quite small

---

### Post by timjohn7 on 2008-04-08
> **oedha said:**
> open terminal, then type :==> sudo dpkg-reconfigure -phigh xserver-xorg
what happen ?

This worked for me partially... I got my projector working but once it was unplugged, I lost my laptop screen and had to go through the reconfig of xorg using vesa settings to get back to a desktop and then use Screens & Graphics to reset my Intel driver.

can you help any further?  Also, just for education, what does the -phigh command do?

---

### Post by matogrosso on 2008-04-25
MikeSz,

I have tthe same problem. Please how did you solve it ? 
The screen is fine but I can t see the bottom of it. 


Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Many thanks,
Matogrosso

---


---
title: "Powerbook G4 right click solution"
date: 2007-02-10
forum: Apple PPC Users
---

### Post by jaha on 2007-02-10
Hi,
I'm found solution for right click problem on Powerbookl aptops.  :)
In file /etc/X11/xorg.conf :
Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	.
	.
	.

change option variable to following value :
	Option 		"TapButton1" 		"3" 
	Option 		"TapButton2" 		"1" 
	Option 		"TapButton3" 		"2" 

Now you have to restart system.
Try once tap on touchpad. and you will have same result as right click on mice.
On Powerbook we have left and right button  but both works as left click.
This is better solution then F12 :)

---

### Post by dpny on 2007-02-12
I tried this on my Pismo and it didn't work. Is there a difference in the trackpad for G3 and G4 laptops of which I'm not aware?

---


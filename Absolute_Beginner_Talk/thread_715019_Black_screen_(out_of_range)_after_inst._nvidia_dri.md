---
title: "Black screen (out of range) after inst. nvidia driver GeForce 6600/LG Flatron L1953S"
date: 2008-03-04
forum: Absolute Beginner Talk
---

### Post by baly on 2008-03-04
Hi,
I installed ubuntu 7.10 yesterday.

After starting up I then installed the official nvidia driver. (GeForce 6600)

Then after rebooting I only get a black screen, but everythings running. (I can log in ...)

The monitor (LG Flatron L1953S) shows:
> out of range
68,6 kHz / 85 Hz

What must I exactly do to fix this?
Please explain it to me step by step because I'm new to this.
:)
Thank you in advance!
-baly

---

### Post by philinux on 2008-03-04
Easiest way is to open synaptic and install then run startupmanager.

---

### Post by sayakb on 2008-03-04
Open terminal and type
```
sudo gedit /etc/X11/xorg.conf
```

Find the section "Screen" and add these 3 lines within the section:
```
	SubSection "Display"
		Modes		"1024x768"
	EndSubSection
```

---

### Post by baly on 2008-03-04
Thanks for the quick answers. 

How do I get into the terminal?

Because when I boot normaly I cant see anything -> so I cant go into the terminal  :)

---

### Post by PmDematagoda on 2008-03-04
Boot Ubuntu in Recovery Mode and then reconfigure the X-Server using:-
```
sudo dpkg-reconfigure xserver-xorg
```
and select the proper resolution and refresh rate, after that is done check if the GUI works using:-
```
sudo startx
```

---

### Post by baly on 2008-03-04
Thanks a lot. I am going to try tomorrow (=


Where can I enter the mode line?

---


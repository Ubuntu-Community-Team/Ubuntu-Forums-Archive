---
title: "New to BSD &amp; Wifi"
date: 2008-09-07
forum: BSD
---

### Post by radtek on 2008-09-07
I just installed DesktopBSD. Probably the most painless basic install ever of any OS I've ever tried. I like the minimalism of Gnome but KDE is allright too so I'll play with it. I'm looking for stability & security.

Impressed to a certain degree. Very snappy and the package manager reveals vulnerable packages installed.

I have two basic questions: 

Wireless networking... My Toshiba laptop's internal wifi is usb based. With Ubuntu I use Ndiswrapper. I see it isn't supported yet in BSD's NDISulator. Really this could be a deal breaker. And, I'm willing to bet the majority of Laptops currently marketed have their wifi cards wired in via usb.  Just a WAG. Any hope soon for me?

Also, how do I install support for side-scrolling for my touchpad? Not a huge issue, but potentially a deal breaker as well since it is irritating and inconvenient.

Hardware specs provided upon request.

Thanks guys.

radtek

---

### Post by cardinals_fan on 2008-09-07
What is your wireless card?  My Belkin F5D7050USB works great...

---

### Post by radtek on 2008-09-07
It is a Realtek 8187B

Also I installed "libsynaptics" pkg to get scrolling. However, I get this message when I try to open the configuration:

Shared Memory is not accessible.
Please add the option 'UseShm ''true''' into the touch pad section of /etc/X11/xorg.conf

But...

```
Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

blah blah

Section "Module"
	Load  "dbe"
	Load  "dri"
	Load  "extmod"
	Load  "record"
	Load  "xtrap"
	Load  "glx"
	Load  "freetype"
	Load  "type1"
EndSection


Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
	Option	    "Protocol" "auto"
	Option	    "Device" "/dev/sysmouse"
	Option	    "ZAxisMapping" "4 5 6 7"
EndSection        

blah blah


```

Since there was no 'touchpad section' I tried adding it to the end of mouse0 input device section but no success.

---

### Post by cardinals_fan on 2008-09-07
I haven´t got time to look into this now, but don´t worry, I´ll put it on my list.

---

### Post by radtek on 2008-09-07
Thanks- I'll check back.

BTW, the more I fiddle with it, BSD is really attractive.

---


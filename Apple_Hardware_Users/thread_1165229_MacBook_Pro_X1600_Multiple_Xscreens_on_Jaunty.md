---
title: "MacBook Pro X1600 Multiple Xscreens on Jaunty"
date: 2009-05-20
forum: Apple Hardware Users
---

### Post by brianbutz on 2009-05-20
So after spending a few hours trying to figure out why fglrx wasn't working, I've come to terms that I'll be using the open source driver.  It's not the best, but I don't think I need anything too intense.

What I'm looking for is how to setup two xscreen sessions using the open source driver.  I'm not the best at configuring my xorg.conf and sort of just tried to wing it with this, which obviously didn't work and just makes my displays mirror and go 1024x768:

```

Section "ServerLayout"
	Identifier "Main Layout"
	Screen     0 "Screen 1" 0 0
	Screen     1 "Screen 2" RightOf "Screen0"
EndSection

Section "Device"
	Identifier	"Configured Video Device 1"
EndSection

Section "Device"
	Identifier	"Configured Video Device 2"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor 1"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor 2"
EndSection

Section "Screen"
	Identifier	"Screen 1"
	Monitor		"Configured Monitor 1"
	Device		"Configured Video Device 1"
EndSection

Section "Screen"
	Identifier	"Screen 2"
	Monitor		"Configured Monitor 2"
	Device		"Configured Video Device 2"
EndSection

```

I'm using wmii, and was able to get one long virtual desktop using two monitors and xrandr working, but I really just want two separate sessions.  Anyone have experience with this?

---

### Post by maflynn on 2009-05-20
Not without the nvidia proprietary drivers.

---

### Post by brianbutz on 2009-05-20
Are multiple Xscreens sessions only available through nvidia cards?  

I should have been more specific: MacBook Pro 1,1 15" with ATI Radeon Mobility X1600.

---

### Post by cyberdork33 on 2009-05-20
> **brianbutz said:**
> Are multiple Xscreens sessions only available through nvidia cards?  

I should have been more specific: MacBook Pro 1,1 15" with ATI Radeon Mobility X1600.
not really sure what you mean by separate xscreen sessions... 

Are you just trying to get your desktop to span two screens?

---


---
title: "Login screen resolution incorrect - how to fix?"
date: 2006-06-16
forum: Absolute Beginner Talk
---

### Post by u.b.u.n.t.u on 2006-06-16
Hi,

My screen resolution is incorrect when I log in to the stage where the password is. From that point it changes to the correct resolution.

There is a hack whereby I can remove all of my higher screen resolutions from xorg.conf but then later when I want to use them I can't as I had just removed them. That hack has also caused other problems when I tried it like by color depth is permanently stuck on 24bit.

Is there a way of correctly setting the start-up to login screen resolution?

Thanks.

---

### Post by Jucato on 2006-06-16
I had a similar problem to yours. I was able to solve it, but I don't know if this is the correct way to do it:

[http://www.ubuntuforums.org/showthread.php?t=194687](http://www.ubuntuforums.org/showthread.php?t=194687)

---

### Post by u.b.u.n.t.u on 2006-06-16
Thanks but that stopped xorg.conf from loading and I had to use vim to make corrections to xorg.conf from the command/text line.

This did NOT work for me:

```
Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV43 [GeForce 6600/GeForce 6600 GT]"
	Monitor		"G90f+"
	DefaultDepth	24
        Virtual         800 600
	
```

I was testing "virtual 800 600".


This however did work:

```
SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1920x1440" "1856x1392" "1792x1344" "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1920x1440" "1856x1392" "1792x1344" "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
```

I put my preferred screen resolution at the front, "1280x1024" and I deleted the other bit depths, keeping 16bit and 24bit.

---


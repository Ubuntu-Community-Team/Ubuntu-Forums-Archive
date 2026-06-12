---
title: "iMac G5 iSight w/ Radeon x600 Pro"
date: 2015-02-09
forum: Apple Hardware Users
---

### Post by wrenhal on 2015-02-09
I have this iMac:
[http://www.everymac.com/systems/apple/imac/specs/imac_g5_1.9_17.html](http://www.everymac.com/systems/apple/imac/specs/imac_g5_1.9_17.html)

I am hoping that someone here has some insight as to the best way to get this running Linux.
This is what I've tried:
Ubuntu 12.04 Live CD.  Never gets to desktop no matter what yaboot options I've thrown at it.

Ubuntu Mate 14.04 Live CD will boot to an 8-bit color depth desktop but as many of you know, the installer is inaccessible at this color setting.  
Some of the Yaboot options just hang the boot process with CPU errors.  Others get me to the desktop but still with only the 8-bit option.  
Most recent I tried was this:  "live-nosplash-powerpc64 radeon.modeset=1 video=offb:off video=1440x900-32".  This line will still go to an 8-bit desktop.  Now if I add "video=radeonfb:off" to this line that's when I get the cpu errors.  I've tried so many different options that I don't remember many of the other combos.  
Any help is appreciated please.

EDIT:
Also, I do have a Lubuntu 14.04 Live CD that I haven't tried yet.  Does anyone think this might work better?   I'm unable to get back to this until sometime late tomorrow.

---

### Post by rsavage on 2015-02-10
> **wrenhal said:**
> I have this iMac:
Most recent I tried was this:  "live-nosplash-powerpc64 radeon.modeset=1 video=offb:off video=1440x900-32".  This line will still go to an 8-bit desktop. 

You should, I think, be using the radeonfb framebuffer with that.  

Try "live-powerpc64 nomodeset video=radeonfb1440x900M-32" (note the 'M' before -32)

If that doesn't work, what is the output of
```

dmesg | grep radeon

```

and 
```

[COLOR=#333333][FONT=Ubuntu Beta]cat /sys/class/graphics/fb0/modes[/FONT][/COLOR]

```

> Now if I add "video=radeonfb:off" to this line that's when I get the cpu errors. 
You are using KMS with this line.  What happens if you just boot to a console (e.g. add "single" as a boot parameter)?

---

### Post by wrenhal on 2015-02-10
Here's the screen I get with that set of parameters.

---

### Post by wrenhal on 2015-02-10
And here are the results of grep and cat.

---

### Post by rsavage on 2015-02-10
I missed the ":"

[COLOR=#000000]live-powerpc64 nomodeset video=radeonfb:1440x900-32"

or

[/COLOR][COLOR=#000000]live-powerpc64 nomodeset video=radeonfb:1440x900M-32"[/COLOR]

---

### Post by wrenhal on 2015-02-10
Well. The added : got me up into the desktop just fine. Ran the installer and then it froze.

---


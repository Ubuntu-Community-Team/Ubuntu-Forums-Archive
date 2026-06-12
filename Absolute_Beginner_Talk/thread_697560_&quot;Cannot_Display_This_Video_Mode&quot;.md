---
title: "&quot;Cannot Display This Video Mode&quot;"
date: 2008-02-15
forum: Absolute Beginner Talk
---

### Post by wolveirne16 on 2008-02-15
Hi Everyone, so it seems like I've got a fairly serious problem here.

On boot after it loads grub I get an error message of "cannot display this video mode", so of course I go back to the recovery console and edit x with "sudo dpkg-reconfigure xserver-xorg", I've tried about 10 different resolutions with different frequencies. I've also tried different monitors (completely different brands/sizes). 

One thing I have noticed, when at the recovery console and typing startx, it begins to boot before crashing out to the recovery console with "Fatal server error: no screens found". 

I'm posting this here because I have absolutely no clue what to do now, no knowledge of any of the commands and such, so if you guys could help walk me through this, that'd be great.

Thanks a lot.

---

### Post by taurus on 2008-02-15
Try

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by wolveirne16 on 2008-02-15
That command worked before, as in it would run but it didn't fix the problem. I tryed it again but now I'm getting the error message, "xserver-xorg postinst warning: overwriting possibly-customised configuration file; backup in /etc/X11/xorg.conf"

---

### Post by wolveirne16 on 2008-02-15
are there any other thoughts on this?

---


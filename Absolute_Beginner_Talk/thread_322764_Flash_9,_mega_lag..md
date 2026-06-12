---
title: "Flash 9, mega lag."
date: 2006-12-21
forum: Absolute Beginner Talk
---

### Post by SZorg on 2006-12-21
I recently installed Opera 9.10, and I think it installed Flash 9 with it. Maybe, maybe not. 

the about:plugins page of Firefox lists:


```
Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 9.0 d55

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes
```

Before the Opera upgrade (uninstall/install updated), flash worked fine. Now even a simple object moving around a screen runs at a few frames per second. Youtube videos are also way too slow.

Any ideas would be great. :]. You guys are awesome.

---

### Post by pay on 2006-12-21
Can you run ```
glxinfo | direct rendering
```to see if you have direct rendering and post the results?

---

### Post by SZorg on 2006-12-21
Direct Rendering: Yes

although I had to nix the "| direct rending" to get it.


To be noted is that I do run beryl some of the time.



Come to think of it, it might be my drivers -- playing WoW in cedega has been considerably slower.. I'll have to look into that.

---

### Post by SZorg on 2006-12-21
What do you know -- I restarted on a hunch that, perhaps my power-hungry 7800GTX wasn't getting enough and, no, that wasn't the problem. Wasn't sure if the Linux drivers would detect that -- so I rebooted to XP, came back negative but -- upon logging back into Ubuntu, I have full speed flash animations and videos. :].


Problem solved, I guess?

---

### Post by pay on 2006-12-21
That is quite strange. Oh well at least it works.

---


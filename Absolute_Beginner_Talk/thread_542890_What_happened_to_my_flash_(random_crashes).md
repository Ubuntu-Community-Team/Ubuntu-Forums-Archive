---
title: "What happened to my flash (random crashes)"
date: 2007-09-04
forum: Absolute Beginner Talk
---

### Post by thelocust on 2007-09-04
I was so happy when flash 9 came out for Linux, finally I could surf for more than a few minutes with out Firefox crashing on me. But for the past few months it seems like I am right back were I started. If I try to close a page or open a new link when a there is flash media playing (youtube) Firefox freezes and then crashes, and thats if it will open that page in the first place. I seem to have more luck if I stop the media before closing it out. Is anyone else experiencing these problems? What are some possible solutions? Thanks.

Specs:
Firefox 2.(whatever is on the repo's)
Kubuntu Feisty 
Flash 9 installed with Automatix2

---

### Post by bone2006 on 2007-09-04
I'm mostly running the 64bit version of Ubuntu, which flash hasn't officially released it.  When I need to visit a site that has flash, I actually run IE4linux and it has flash integrated, which works perfectly.  I've seen posts before for using IE tab extension while in firefox, which is really nice.  You just go to the site while in firefox and right click on the windows and select open in IEtab and it uses IE's engine and you don't have to leave firefox.

---

### Post by thelocust on 2007-09-04
I was hoping I was having a problem but it sounds like just another case of crappy Linux support.

---

### Post by ryno519 on 2007-09-05
Same problem. Tried installing the latest version of flash (a beta) and I still get the problem. It seems more than a few people are having the same difficulties, but so far I haven't seen a fix for it.

---

### Post by bone2006 on 2007-09-05
To defend linux, I went into synaptic package manger and installed non-free flash and I've never had a problem using this on multiple machines that were 32bit.  Going to 64bit I had the problem as flash didn't release anything linux 64bit.  There is gnash, which is supposed to be a FOSS alternative to flash, but it didn't work too well for me.

So I would double check to see if your running the non-free flash version on the 32bit system.  On 64bit there's a few things you can do, and everything I did broke after awhile, so I'm just using IE4Linux with flash enabled and it works great for me.

---

### Post by zxccvb on 2007-09-05
It seems that this is a problem with the flash plugin itself. Not with firefox. 

You may try to install firefox with wine if everything else doesn't work.
I posted about this temporary workaround here:
[http://ubuntuforums.org/showthread.php?t=543608](http://ubuntuforums.org/showthread.php?t=543608)

Hope to be of any help.

---

### Post by littleiffel on 2007-09-06
Hi, I had almost the same problem, where firefox crashed randomly on Flash Sites. I realized that I had two flash-plugins running.

Could you visit with firefox the about:plugins(Type this as Link in Firefox) page. And check that there is only one Flash Plugin running.

---

### Post by thelocust on 2007-09-06
Sounds good but you didn't provide the link.

---

### Post by littleiffel on 2007-09-07
Sorry it's 

```
about:plugins
```

---

### Post by thelocust on 2007-09-07
Haha I get it. I'll try that, also I used automatix2 to install flash which I recently found out on another thread that it could mess some things up.

---


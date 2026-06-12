---
title: "Preformance of Ubuntu in comparison to OSX"
date: 2008-11-16
forum: Apple Hardware Users
---

### Post by hanzomon4 on 2008-11-16
I'm not sure what it is but Ubuntu is really choppy in comparison to OS X. Scrolling in Firefox for example is not nearly as smooth as it is in Firefox under OS X. The same with flash, it's not nearly as smooth. Compiz is really good, great in fact but the "easy" things seem to trip and at times choke. I'm curious as to why this is, macbook pro 3.1 Ubuntu 8.10

---

### Post by IQRules on 2008-11-16
> **hanzomon4 said:**
> I'm not sure what it is but Ubuntu is really choppy in comparison to OS X. Scrolling in Firefox for example is not nearly as smooth as it is in Firefox under OS X. The same with flash, it's not nearly as smooth. Compiz is really good, great in fact but the "easy" things seem to trip and at times choke. I'm curious as to why this is, macbook pro 3.1 Ubuntu 8.10

Do you use boot camp / parallel or native install?

---

### Post by y@w on 2008-11-16
I haven't tried Ubuntu on a MacBook Pro so I guess I'm not sure but it might be some driver issues. There's some documentation on the MacBook Pro hardware in the wiki: [https://help.ubuntu.com/community/MacBookPro](https://help.ubuntu.com/community/MacBookPro)

Also, I just thought it would be worth mentioning that Phoronix did a comparison between Ubuntu an OS X on a mini. It seemed that video performance on Ubuntu was not nearly as good as OS X: [http://www.phoronix.com/scan.php?page=article&item=ubuntu_macosx&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_macosx&num=1)

---

### Post by hanzomon4 on 2008-11-17
It's a native install (I used diskutility not bootcamp) I remember reading some where that 2d on nvidia cards sucked... Maybe that has something to do with it

---

### Post by bryonak on 2008-11-17
The Firefox scrolling issue is a bug between Firefox3 and the X server.
The new Firefox requests redrawing elements in such a way that X paints them hundreds of times over, causing your CPU usage to spike up when scrolling (this is obvious if you take a look at the System Monitor).
I've read that the fault actually lies with the Xorg people, but they're not going to fix now. Rather it in some upstream release in the future, since it's not critical and they need their time for other tasks.

Flash... well you hit a soft spot there.
It's controlled and distributed by Adobe, who doesn't care about realeasing quality codecs for Linux. It uses way too much CPU and they don't even have 64bit support.
The open source alternatives lack many advanced features, so Adobe's implementation is mostly used, though being what some devs I know call crappy.

Try scrolling in any other browser (let's say WebKit based ones... or even your file browser), it will not be as sluggish as in Firefox.
This issue will be resolved, as for Flash we can only hope.

---


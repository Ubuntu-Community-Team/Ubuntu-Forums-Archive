---
title: "slow start up after fresh installl"
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by pixelstuff on 2008-02-24
Hello
After a fresh install my Gutsy, which was very fast before, takes at least double time to start. :popcorn: I also don't see the loading bar  like before. Once up the speed is normal. Where can I start to find out what the reason is?
Thank you

---

### Post by slimdog360 on 2008-02-24
did you install the amd64 version or the i386?

---

### Post by pixelstuff on 2008-02-24
It's the i386

---

### Post by pixelstuff on 2008-02-25
bump
:rolleyes:

---

### Post by parmdeep on 2008-02-25
i noticed this slightly however once i updated ubuntu everything was back to normal, have you enabled all the updates in synaptic?

---

### Post by Cha1n5aW on 2008-02-25
I'm running gutsy 7.10 and I find it very slow to start up as well.  I dont even get the ubuntu splash screen, just a blank screen for about 10 minutes, then I get the login page.  I haven't really figured it out either, maybe there is a log of everything that goes on during startup, I've no idea where to find such a thing if it even exists.

- Shawn

---

### Post by Abacab on 2008-02-25
Slimdog, is there a reason why you asked if it was amd64? I only ask because my start up time is quite slow with no loading screen and I'm using amd64.

---

### Post by pixelstuff on 2008-02-25
I have all updates enabled, also the pre-released and unsupported ones.

---

### Post by lila on 2008-02-25
I had the blank screen problem as well, 
[http://ubuntuforums.org/showthread.php?t=656978](http://ubuntuforums.org/showthread.php?t=656978)
this helped a bit.  Not totally happy, but it's better than it was.
Lila

---

### Post by philinux on 2008-02-25
Click the link below for known bugs, slow startup is one on some hardware.

---

### Post by pixelstuff on 2008-02-25
phil, I dont think its on the hardware in my case because the system was fast up before the fresh install when I had a gutsy upgrade. :confused: I also noticed that when I do Strg Alt F1 now I suddenly get a freeze and a weird console view with huge fonts. That was all different before, in fact I upgraded to gutsy from Strg Alt F1 and it always worked. I'll have a look at Lilas thread tomorrow. (Does nobody by default have splash screens on Gutsy?)

---

### Post by incen on 2008-02-25
If you didn't see the loading bar, I think maybe you got into situation like mine.
Do you have startupmanager? If you don't, then you can try to install it by
```
sudo aptitude search startupmanager
sudo aptitude install startupmanager

```
> Using startup manager, you can change the resolution. Change it to 1024 x 765. If it is on 800 x 600, then you'll never see it.
And then use it to pick up the resolution for booting/loading page. Although it looks fine in OS after login, it has different application controling the booting/loading.
You can refer to this thread:
[http://ubuntuforums.org/showthread.php?t=702753](http://ubuntuforums.org/showthread.php?t=702753)

---

### Post by pixelstuff on 2008-02-26
That was it in my case! Starting up again even quicker than before the fresh install! Strange that the weird resolution (or maybe what caused it) made not only the bar disappear but also slowed everything so much.

---


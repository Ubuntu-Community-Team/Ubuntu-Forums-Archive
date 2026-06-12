---
title: "screen resolution"
date: 2008-03-27
forum: Absolute Beginner Talk
---

### Post by odwyerda on 2008-03-27
evening all, 
I have been running Ub for about 2 weeks now ( acutally im using Wubi but thats because ive not spare cds at the mo). This maybe trivial but....

Everything is working perfectly but my screen resolution is well blurry, the only way to describe it is that its like i have vaseline over my screen ( there isn't :) ) i am wondering if there is a way to make it sharper

Details

feisty Fawn
Compaq Pessario V5000
1gig ram 
celeron processor m 1.46ghz
Dual boot windows Xpsp2

Need any other details

Dave
Thanks in advance

---

### Post by OffAxis on 2008-03-27
what kind of video card do you have?
What kind of monitor?

Can you post a screenshot?

---

### Post by odwyerda on 2008-03-27
I have a Intel 9g45 express video card.


i cant tell if thats what i see or not of course. it should not be too sharp like what ive seen on other systems
Runing on my setting of 1024*768

---

### Post by OffAxis on 2008-03-27
I hate to say it, but your screenshot looks pretty decent on my monitor.

Is the appearance of XP significantly better?
If it's not it could be a hardware problem (backlight burnout?), if it is better than it may just be a settings problem (driver, power saving or color saturation).
What driver are you using?
I don't know if one's available for that chipset, but you could try the 'Restricted Driver'. It's a checkbox in the 'System Settings' somewhere.

There's the standard command of 

```
sudo dpkg-reconfigure xserver-xorg
```

which will let you change any options relating to the xserver (including screen resolution, refresh rate, and driver).

> Runing on my setting of 1024*768
Are you sure your monitor supports that setting? It may be trying to do a 'best fit' approach...

---

### Post by lawentzel on 2008-03-27
OffAxis hit the nail on the head.  I suspect the problem is the refresh rate.  See what it is set at, and change it.

---

### Post by Bölvaður on 2008-03-27
The screenshot is ok.
What I'd suggest to you is change resolution, fonts, colour theme... etc. Everything that might have anything to do with this. If you change 1 thing at a time you might find out exactly what is wrong.

---

### Post by odwyerda on 2008-03-31
Right I think I resolved it, had something to do with the display effects, when I turned it on everything became crisper like my xp desktop,
And everything is just better looking.

Many thanks for the help , suppose this is solved.

:):):):):):)

---


---
title: "xubuntu is crazy slow...help"
date: 2008-01-07
forum: Absolute Beginner Talk
---

### Post by tx302 on 2008-01-07
Total xubuntu newbie, and I'm totally confused.  The reason I installed this is because I was told it could help an older laptop (ThinkPad T20 w/ 400mhz, 192mb) run pretty efficiently.  I've read lot's of threads online, but haven't had any luck so far.  Things are 3x slower in xubuntu (gutsy gibbon) as they were in WindowsXP---obviously this doesn't make sense, so there must be some setting that's out of whack.

Can someone please help me diagnose the problem? Desperate here...

---

### Post by jba6511 on 2008-01-07
what do you mean by slow? Is it only certain apps? internet connection speed? overall the system is sluggish and unresponsive?

---

### Post by (((X))) on 2008-01-07
is it slow with live cd or bootingup slow, running applications slow..what is so slow?

---

### Post by tx302 on 2008-01-07
Whole system.  Even when I click on the Applications drop down menu, it stalls for a good 5 secs before it opens.  Firefox takes a few minutes to load.  The hard drive seems to be thinking quite a bit when I access anything.  Tried doing some hdparm tweaks but they didn't improve anything.

edit: I may not have done the hdparm tweaks correctly, though...

---

### Post by Phantom784 on 2008-01-10
I've noticed this too on an older machine I put Xubuntu on.  Much slower than windows, or even regular Ubuntu which i've had on it before.  I'm using Gutsy btw,

---

### Post by perlluver on 2008-01-10
Try DSL, or Puppy Linux.

---

### Post by kerry_s on 2008-01-10
> **tx302 said:**
> Total xubuntu newbie, and I'm totally confused.  The reason I installed this is because I was told it could help an older laptop (ThinkPad T20 w/ 400mhz, 192mb) run pretty efficiently.  I've read lot's of threads online, but haven't had any luck so far.  Things are 3x slower in xubuntu (gutsy gibbon) as they were in WindowsXP---obviously this doesn't make sense, so there must be some setting that's out of whack.

Can someone please help me diagnose the problem? Desperate here...


with those specs it's always going to be slower than windows with a equal amount of programs. i run in just about the same specs, just a tad better. unless you use a linux designed for old monsters like ours or doing a custom install with only what you need, it will always be slower. linux is a choice, it's not always the best for certain hardware.

---

### Post by tylerspaska on 2008-01-10
i had this same problem on a desktop with similar specs (450 Mhz and 256 MB ram). i set up conky to help me with the problem. for me the problem was amarok, the music player. for some reason it was using 50-100% of the cpu ALL the time. i turned it off and use xmms with a cpu idle load now below 10%.

the bottom line is that you probably have some runaway program using up all your cpu and always writing to the disc. diagnose and replace that program if possible. if that isn't possible then i would go with 'damn small linux'. i think it's great.

to set up conky:
[http://ubuntuforums.org/showthread.php?t=205865](http://ubuntuforums.org/showthread.php?t=205865)

---

### Post by tx302 on 2008-01-10
thanks for all the input everyone.  For the record here's what ended up happening...I reinstalled Xubuntu to see if that would help at all---no luck, still slow.  So then I formatted and installed Suse---kinda slow (but not as slow), but I couldn't get the wireless to work, so I formatted again.  Then, I installed Windows 2000...and it runs like a champ.  I'm a bit disappointed I didnt' have a better trial run with Linux, but oh well.  Pretty impressed so far with Win2k.

---

### Post by kerry_s on 2008-01-10
> **tx302 said:**
> thanks for all the input everyone.  For the record here's what ended up happening...I reinstalled Xubuntu to see if that would help at all---no luck, still slow.  So then I formatted and installed Suse---kinda slow (but not as slow), but I couldn't get the wireless to work, so I formatted again.  Then, I installed Windows 2000...and it runs like a champ.  I'm a bit disappointed I didnt' have a better trial run with Linux, but oh well.  Pretty impressed so far with Win2k.

you can't go wrong with win2k on a low resource system, stick with win2k, xp takes alot of tweaking to get the same performance and low resource use. just pick your applications carefully and it will stay speedy.

here's a pic of my app's, i'm to lazy to type them out. all are low resource.

---

### Post by phinn on 2008-01-11
I have the same problem with this old useless Dell L433c at my work. (Celeron 433MHz, 192mb ram) I threw on Xubuntu at my work thinking I could "revive" it and it would run all nice.  Nope.  Windows 2000 runs like 3-5x faster at almost everything. In Linux watching a video is impossible (it's like a slideshow) and I can't even imagine how bad Gnome would be.  I guess its that X.org doesn't support the crappy i810 embedded chipset this thing has in it. I tried a lot of tweaks to but it didn't help all that much.

I wish there is more I can do. I usually use Linux anyway just because I like it, but I can't say, in this case, it's better =/

---

### Post by K.Mandla on 2008-01-11
It's a common misconception that Xubuntu is going to run happily on 500Mhz machines and lower. Xubuntu has shifted toward the same Gnome software and structure that makes up the full Ubuntu suite, and it lost a lot of its speed in the process. 

On the other hand, there a **lot** of other distros, some Ubuntu-based, that might work well on your system. Consider. ...

[http://ubuntuforums.org/showthread.php?t=575456](http://ubuntuforums.org/showthread.php?t=575456)

---

### Post by HemiGTX on 2008-01-11
here's a great alternative to xubuntu.. 
[http://www.xfld.org/](http://www.xfld.org/)
its a pure xfce4 install with very few gnome dependnecies..i have it runing quite well on a Compaq Armada M700 P2 399mhz with 128mb ram 4mb ati video chip and 6 gig hdd :)

it is built on 6.10 not 7.10 but ive had no problems at all

---


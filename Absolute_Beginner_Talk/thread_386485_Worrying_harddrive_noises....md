---
title: "Worrying harddrive noises..."
date: 2007-03-17
forum: Absolute Beginner Talk
---

### Post by neocookie on 2007-03-17
Hi all

I'm getting a little worried about noises from my hard drive on my laptop. It seems to be doing a lot of scanning for data, and when it does finally power down its usually with a clunk.

I've got more than 512Mb ram in there, and I've got some hdparm settings in my /etc/rc.local which I hope are helping out:
hdparm -c3 -m16 -S60 /dev/hda

I've tried other settings, but I usually get a hard lock. If i drop those, my hdd seems to never spin down, which again is worrying.

Is there anything I can do to help out? Maybe do some sort of defrag, or any other hdparm settings I can try? Or are there any daemons I can run while will manage my hdd?

Thanks.

---

### Post by halw on 2007-03-17
Make sure you are doing regular backups and start researching a replacement hd. Sounds like your drive is going south.

Hd's are not a difficult thing to swap in a laptop. Just do your homework and you should be fine. You should be able to find adequate information at the laptop vendor's web site on how to remove and insert the hd.

---

### Post by diepruis on 2007-03-17
Yeah... I agree. Once they start doing that it's pretty much over for the drive.

---

### Post by neocookie on 2007-03-18
I can't believe its that - I've only had the laptop for about 6 months, and while it gets quite heavy usage (i use it most nights) its no left on 24/7 and i'm not using anything that would use the drive a lot (like DV editing, P2P s/w, or anything).

Any way I can be sure it is that?

---

### Post by diepruis on 2007-03-18
You could've gotten a bad drive, though. Also, holding the laptop at odd angles while it's on can have that effect.

It should still be under warranty, however, so why don't you take it in and let the hardware professionals have a look for you? I can't really offer much advice as I'm mostly a software guy.

---

### Post by hardyn on 2007-03-18
Yes... a few ways...

-let somebody with experience listen to it.
-pay attention to odd hard disk indicator activity (led)
-use a hard disk util to scan the media suface (usually windows, usually free)

i have been wrong before, but your drive sounds fine...

are their any other symtoms or just a clunk at power down?  that is actully pretty normal... the read heads 'park' at power down... the heads are moved off the writing surace, so in the case of a bump the heads do not contact the writing surface.

the hard disk does not spin down for the most part, only if 'laptop' mode is enabled in the apci config file... and then its VERY agressive, you probably want to edit that file otherwise it spinds the drive down every 5 sec!

playing with hdparm is REALLY agressive... it actully lets you control alot more of that disk that you should... be really careful using it!

6 months is not common for a hard disk failure, but not uncommon at the same time.  anything that will fail will do so inside of the first year... if it makes it outside the first year, it will probably hast for 2-3.  keep in mind also that all note book harddisks run warmer than the manufacturers recommend, hard disk failures on notebooks are quite common... heat and the agressive power saving schemes that are often used, spinning up and spinning down the harddrives sereral times an hour is quite hard on them.  hard drives only have like 500000 power cycles in them before the servo fails.

if you have only had it 6mo, and it does turn out to be bad, it should still be under warranty ;)

---

### Post by neocookie on 2007-03-19
I'll turn off my hdparm settings and leave it for a month, see how I get on. It needs to go back under warrenty anyway - the screen's powerlevel/backlight changes dramatically when i adjust the screen angle, which can't be right.

---

### Post by akshunj on 2007-04-19
Hard drives are like a box of chocolates.  You never know what you're gonna get.  6 months or six years, I've had them go out at all different times.  If it's got moving parts, it can get screwed up.

--Akshun J

---


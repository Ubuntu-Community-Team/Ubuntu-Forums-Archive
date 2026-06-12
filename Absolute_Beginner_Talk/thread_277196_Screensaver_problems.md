---
title: "Screensaver problems"
date: 2006-10-14
forum: Absolute Beginner Talk
---

### Post by blenheim46 on 2006-10-14
I've just installed Ubuntu Dapper (6.06?) and all seems fine except for one thing, if I leave it on and the screensaver kicks in then everything freezes and locks up if I reboot everything is ok as long as i don't let the screensaver kick in, any ideas? I'm not sure what info you will want but i got my copy off the PC Answers 164 dvd

---

### Post by meng on 2006-10-14
Well one obvious answer is to disable the screensaver ...
Is this a notebook computer? Could it be that some powersaving feature is being triggered? APCI support in Linux I understand still has some glitches.

---

### Post by blenheim46 on 2006-10-14
No I have it installed on a spare 45gig harddrive in my main pc if I go into the screensaver it locks up as well

---

### Post by meng on 2006-10-14
Graphics card? RAM?

---

### Post by blenheim46 on 2006-10-14
radeon 9800 pro and 1gig of ram

---

### Post by chroniker on 2006-10-18
I thought that vid or ram was my problem, and may very well be, because I've got a lesser vid card (64meg) and not near 1.0G (128meg) RAM. So I'm thinking my problem is hardware compatibility with my vid card.

I was finaly able to get to ss settings quick enough to disable it, but I nearly went bonkers getting there.

---

### Post by dca on 2006-10-18
Can you access your BIOS and disable power-save from there to assist in diagnosing?

---

### Post by caravel on 2006-10-18
I'm guessing you're having the same problem as I was, expecially seeing as you have a Radeon.

Look half way down the first page of this thread onwards, after the 60Hz problem is resolved:

[http://ubuntuforums.org/showthread.php?t=276650](http://ubuntuforums.org/showthread.php?t=276650)

---

### Post by CatKiller on 2006-10-18
```
gconf-editor
```
/apps/gnome-screensaver/
uncheck idle_activation_enabled

To turn the screensaver off in the meantime.

Sounds like a driver issue. Follow one of the threads to get your fglrx drivers installed, and try it again once you've got the graphics running without problems.

---

### Post by chroniker on 2006-10-18
After I made my post above I was thinking drivers too.

---

### Post by mcduck on 2006-10-18
Do you have fglrx drivers installed? If not, make sure you are not using any OpenGL-based screensavers (or random setting). The default ati driver in Ubuntu doesn't provide 3D acceleration with Radeons.

And then of course you can install fglrx and get the 3D working :)

---

### Post by chroniker on 2006-10-18
The reason for my post was to let the OP know that he was not alone on this. For me, not being able to look at the neato designs on my screen is not that big of a deal so unless I start having other video problems I'm not going to worry about. However I do realise that the more I start using linux I will eventually have to fix this.

Besides, if I'm looking at a screensaver I'm not learning linux (and having said that, I just shot this entry out of the water).

---


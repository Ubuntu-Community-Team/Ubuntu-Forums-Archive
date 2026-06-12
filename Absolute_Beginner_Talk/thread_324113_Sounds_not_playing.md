---
title: "Sounds not playing"
date: 2006-12-23
forum: Absolute Beginner Talk
---

### Post by LIJI on 2006-12-23
Hey,
For some really weird reasons, the only sounds Ubuntu plays is the Ubuntu system sounds (such as startup, shut down, etc) and the example ubuntusax.ogg file.
Any other sound, including Firefox flash objects, Wine apps and some Players won't play sound and majorly slow down the app every time a sound should be played.
Tested on:
Youtube on Firefox
A video site on Firefox
A chat program using Wine
A .mid file using ALL sound players that can be found on Add/Remove.

How can I fix it?

Thanking in advance
-LIJI

---

### Post by LDRoamer on 2006-12-23
I don' t know if this will help you but the following link provides some suggestions for troubleshooting sound:

[https://help.ubuntu.com/community/DebuggingSoundProblems](https://help.ubuntu.com/community/DebuggingSoundProblems)

I had real trouble with my sound and only got it working by trial and error. In my case I have the exact sound chip described in the above link.  Following the directions exactly did not result in sound for me. Through trial and error I found out that the dma2 setting needed be set to dma2=0 instead of 5 as indicated. In my case using the tutorial in the link above told me it should be set to 5 but it wouldn't work. I tried using 2 but that gave me sound and no floppy. I am not suggesting that any of this is useful to other than to suggest you many need to do some experimenting. In my case I am running Ubuntu on an old laptop and that  has a couple of buggy bits of hardware in it.   Others with more knowledge may be able to help you more. I am still pretty new at this linux stuff.

---

### Post by bcs on 2006-12-23
I am experiencing a similar problem: embedded videos in Firefox sometimes have sound and sometimes do not...all other sounds (system sounds, CD's, etc.) work consistently as far as I can tell...

---

### Post by bcs on 2006-12-23
I think I've figured a way to get my sound working consistently (if not perfectly)...I shut down all other apps (including apps that don't seem to need sound card, e.g. Thunderbird) and issed the following two commands:

```
sudo killall artsd
sudo killall esd

```

restarted Firfox and video sound works!  Evidently, there can be an issue with some apps locking others out of sound card use...I found all that info, including the commands, in [this thread]("http://ubuntuforums.org/showthread.php?t=323820&highlight=video+sound")

Like I said, closing other applications is not optimal, but if it works consistently, it's fine with me...

---

### Post by LIJI on 2006-12-24
I still don't get it to work. :(

---

### Post by TooRight on 2006-12-24
You might want to try "alsamixer" in the terminal and check to make sure the sound isn't muted (MM)

---


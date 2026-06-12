---
title: "un SOUND decision - now silence!"
date: 2007-02-22
forum: Absolute Beginner Talk
---

### Post by freebird54 on 2007-02-22
Here I thought I knew a little bit what I was doing now - how wrong!

Got my ATI card to work, made GRUB pretty, with a dual drive, triple boot system, started making the desktop look like home - THEN I discovered Automatix.

THought, well - get 'em all, try 'em, throw away the ones unliked/unneede.... now I have no sound at all!

Is there a discussion of which apps work with which drivers, and how the drivers interact with each other?  Of which way to go with fairly simple needs music wise?  Of how to get back to the beginning, when I could at least hear the drums, and play an audio CD???

I only want the Sounds of Silence when listening to Simon & Garfunkel.....:guitar: 

freebird54

BTW - system is AMD 1GHz on ASUS A7S MB, 512Mb RAM, 150 and 40 Gb drives, and running triple boot Win98SE, XP Pro, and Edgy (destined to replace the other 2)

fb

---

### Post by AtrejuT on 2007-02-22
Hi Freebird,


what soundcard are you using? The thing responsible for sound is called ALSA, there's already a couple threads around explaining how to get it to work.

The first thing you should check is running 
```

alsamixer

```
in a terminal and check if Master and PCM are unmuted and turned up. (They are muted if at the bottom of the bar it says MM, they are unmuted if it says OO and is green.

atreju

---

### Post by freebird54 on 2007-02-22
I am running a Sound Blaster Live! value  (I believe that's what they call it) - almost boringly standard.  Basic sound worked fine before I looked at it!

I have tried setting things to OSS, and back to ALSA , and nothing that I can find through System->Preferences->Sound or from the 'Volume Control' shows anything muted - and the CD sliders and others are all at maximum.

I have started to uninstall things, but I'm sure it won't be that simple as I have already removed most of what I optimistically added....

freebird54

---

### Post by AtrejuT on 2007-02-22
Hey freebird,


go slowly on the uninstalling and lets first have a look around:
what does
```

aplay --list-devices

```
give you?

I won't be online much longer I'm afraid, have to go to university, but there's a rather comprehensive Wiki page on solving sound problems here: 
[https://help.ubuntu.com/community/Sound](https://help.ubuntu.com/community/Sound)

atreju

---

### Post by jackrobinson on 2007-02-23
> **freebird54 said:**
> Here I thought I knew a little bit what I was doing now - how wrong!

Got my ATI card to work, made GRUB pretty, with a dual drive, triple boot system, started making the desktop look like home - THEN I discovered Automatix.

THought, well - get 'em all, try 'em, throw away the ones unliked/unneede.... now I have no sound at all!

Is there a discussion of which apps work with which drivers, and how the drivers interact with each other?  Of which way to go with fairly simple needs music wise?  Of how to get back to the beginning, when I could at least hear the drums, and play an audio CD???

I only want the Sounds of Silence when listening to Simon & Garfunkel.....:guitar: 

freebird54

BTW - system is AMD 1GHz on ASUS A7S MB, 512Mb RAM, 150 and 40 Gb drives, and running triple boot Win98SE, XP Pro, and Edgy (destined to replace the other 2)

fb
run
```
alsamixer
```
and **unmute PCM**

---

### Post by freebird54 on 2007-02-26
Well - after a LOT of Googling, HOW TO following and diagnostics here is the result.

I HAVE SOUND!

However - I still don't know what broke, or what actual item actually fixed it!

Most likely follows however - it may help someone.

alsamixer - turn EVERYTHING ON even the PC speaker - anything with a slider goes UP.

Now to the next problem (they're getting fewer all the time)

freebird54

oops - forgot to mention I returned everything to 'AUTODETECT' in System->Preferences->Sound except Capture (ALSA)
FB

---

### Post by ygarl on 2007-02-26
Hahah... You need to be more careful with your fault-finding, my friend.
What you have done is the equivelant of your car not starting - so you replace every single part in the engine... then try to see if it will work!

Try one thing - test, try another - test. Otherwise, you might have eventually just reinstalled - when all you may have needed to do is just change a few settings.

Good luck!

---

### Post by freebird54 on 2007-02-26
Ah well, it hasn't been a bad run over the years.  Normally it is best to start with undoing the last thing you did before the problem - and then redo it more slowly  :)

So far 5 problems and 4 fixes - and only 1 of them required a re-install!  Not bad for a newbie I thought.  I was especially pleased with 1 I got on my own (never saw it mentioned directly in any post/forum/HowTo etc.

Funny how the solution is always in the last place you look!

Oh, wait a sec - when you find it, you stop looking!!

Now to come up with a useful sig...

freebird54
----------------------------------------------------------------------
AMD Athlon 1GHz, 512Mb RAM, 256Mb ATI Radeon 9550, 150Gb & 2x40Gb drives, Sound Blaster Live! Value, Panasonic KXP-4400 Pinter, triple boot Ubuntu--Kubuntu--XP Pro

---


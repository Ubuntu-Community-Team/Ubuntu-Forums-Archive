---
title: "Cruddy Sound + Weird Boot Issue"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by Toupee on 2007-04-23
Hi guys.  Just installed Feisty today, and really liking it.  I've toyed with Ubuntu just a wee bit before and spent some time in freeBSD in the past.  I've been having trouble with two things that I just can't figure out.

1. I can only get Ubuntu to boot in recovery mode!
If I try and boot Ubuntu regularly, all I see is 'kernel alive' and then immediately my monitor cuts out and says 'no signal.'  I have no idea why this is.
If I boot into recovery mode, all I have to do is startx and everything works fine.  The only real problem is that being stuck as root is a little unsettling.

I have an ATI X800 video card.  I did install the fglrx drivers but they don't really work for me.  At all.  The screen just goes insane when I boot X.  It's completely unusable.  I've simply changed 'ati' to 'radeon' and X works fine like that.  I WOULD kind of like to get 'fglrx' working because I'd like to mess with compiz/beryl a bit and I'm guessing I need to use that.


2. More important to me right now, my sound is crap.
Music sounds fine.  Everything sounds fine.  Sort of.  It's just that there's this constant level of weird, scratchy, fuzzy, static-y sound that's ALWAYS there.  It cuts out when ALSA shuts down, I've noticed.  I don't even want to attempt to act like I know anything about sound in linux.  In fact I'm really confused about the whole sound process.  Could I muck about with PulseAudio - or is that for something else entirely?

My sound card is an ensoniq.  It's certainly not top of the line - but it produces otherwise completely crisp and clear audio in Windows.

Thanks in advance... I'd really appreciate any help.

---

### Post by mikeyphi on 2007-04-23
Did you see this message about ATI cards?  [http://ubuntuforums.org/showthread.php?t=414194](http://ubuntuforums.org/showthread.php?t=414194)

Try here for your sound problem:  [http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide](http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide)

---

### Post by Toupee on 2007-04-23
Thanks - I did try the ATI thing but no luck.  If anyone has any other ideas, that'd be great.

I actually figured out the sound problem.  All I had to do was open alsamixer and I noticed I had a 'PCM' and a 'PCM 1'.  I lowered the PCM 1 volume all the way and eureka... crisp sound.  I feel so much better.

Oh yeah.  My sound card is an Ensoniq ES1370.  Maybe this will help someone in the future.  I've been having this problem for years in both BSD and Linux.

---


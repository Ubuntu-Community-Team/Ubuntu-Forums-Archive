---
title: "Question Concerning Sound"
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by Cyann0923 on 2007-05-27
I have been having some issues with my sound, I know it's cliche.

I have a Diamond Xtreme Sound 7.1/24 bit sound Card. I can't find drivers for ALSA for it anywhere. I also have an Asus AN832-SLI  Deluxe MotherBoard.  The built in audio doesn't work at all in it, but if it would be better to use, Let me know.

I had my sound working okay, and didn't have many problems.  Then a few days ago, some programs stopped working with it. XMMS, Amarok, and VLC. I had to use Audacity to hear any music.  Then Everything started working, but Web pages stopped.   Then VLC started getting scratchy.  Then everything stopped working.  Then Just Amarok. 

I've been going on like this for the past few days and I am about to lose it.  Everytime I reboot, something doesn't work.  XMMS and some of my video players say that something else is using my Audio device, which I don't think is true, although I really have no clue.

When I go into my sound config,  the only option that works is OSS,  but I'm pretty sure I wanna be using ALSA.  I am a musician,  and I wanna be able to use my audio programs.  It's kinda my thing.  If anyone can lead me in the right direction,  that would be cool.  I don't think I set up anything correctly,  since I just dove in without doing proper research.  When I fix this,  I will have Kubuntu doing what I want (minus the fact that anything that uses Xine plays all my video blurry) and that gets me excited.

Thanks in advance.

---

### Post by Happy_Man on 2007-05-27
You have tried typing in ```
alsamixer
``` into a terminal, right?

---

### Post by Cyann0923 on 2007-05-27
Yes,  nothing changed.  everything was at normal.  I adjusted some things,  moved to independant,  then back,  nothing changed.

Edit: after restart, everything worked. I don't know how long this will last, but I made sure that everything (kmix, alsamixer, sound preferences, and all players) had ALSA chosen for audio)

Thanks Happy_Man for pointing the alsamixer thing out to me.

---


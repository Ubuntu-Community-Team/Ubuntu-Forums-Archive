---
title: "Lubuntu 12.04 - No Sound After Suspend"
date: 2012-08-14
forum: Apple Hardware Users
---

### Post by JustYakov on 2012-08-14
I installed Lubuntu 12.04 onto my iBook G4, and while everything's fine and dandy, but there's one annoying problem, and that is that there's no sound after resuming from suspend. If I restart the computer the sound comes back on, but nothing else works. I tried:
[LIST]
[*][FONT="Courier New"]rmmod snd_powermac[/FONT], but it says that it's being used
[*][FONT="Courier New"]alsa force-reload[/FONT], but it fails to unload some modules, including snd_powermac
[*]Restarting alsa-utils, but that doesn't even exist!
[/LIST]
So, anyone has a solution/suggestion or am I stuck with half-working sound?

---

### Post by 2blue on 2012-08-15
Have you tried something very simple like opening alsamixer and checked if some kind of setting for some weird reason has changed?

---

### Post by JustYakov on 2012-08-15
Yeah, I checked alsamixer and it doesn't seem like anything's muted. I also installed pavucontrol to monitor sound-playing applications and it plays as if nothing is wrong.

---

### Post by 2blue on 2012-08-15
Very strage, I have not ran into the same issue my self, and cannot think of a thing that can cause it. I had trouble with no sound right after lubuntu install, there was no alsamixer in thermial, not a thing. I had to reinstall alsamixer and I was guided to a ppc *** page with suggestion for fixed. I ran some sudo commands I cannot remember at the moment and sound has been fine since. I also have a G4 iBook. [Here]("http://ubuntuforums.org/showthread.php?t=2020131&highlight=G4+iBook&page=2") is a link to the help I was given, if it applies to your situation.

---

### Post by JustYakov on 2012-08-15
Thanks for the help, but that doesn't seem to be the issue. Everything is working absolutely great, and that glitch is the only problem on this computer.

---

### Post by andrewhamming on 2012-08-21
I have the exact same issue. A solution would be great :)

I am using sound blaster live card

---

### Post by obstruction on 2012-11-08
Has anyone had any more insight on this issue?  I am experiencing exactly the same thing, with my PowerBook G4 and the standard sound card -- audio works fine until I suspend, then it stops working.  After a restart, it works fine.

However, I did notice a tiny bit of sound coming out of my speakers while playing an mp3 in VLC.  Sure enough, after I boosted the preamp in the EQ settings, and plugged the computer into an external stereo amp, and cranked the volume up all the way, there was my mp3 playing, very, very quietly! 

So, at least on my system, the issue is technically very very quiet sound after suspend.  Any ideas on what would make that happen?

---

### Post by imixmuan on 2012-11-19
Exactly the same issue in Lubuntu 12.04, ibook G4 1.07 ghz. Sound is muted on waking from sleep, barely audible. Reboot fixes the problem. Any solution greatly appreciated.

---


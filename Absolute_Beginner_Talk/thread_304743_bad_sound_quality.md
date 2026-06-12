---
title: "bad sound quality"
date: 2006-11-22
forum: Absolute Beginner Talk
---

### Post by MaximB on 2006-11-22
ever since I started using Linux (5 months now) I have a bad sound quality
I use edgy and most of my mp3 sounds very bad.
I have a regular built in sound card (I don't know which).
the strange thing is that the sound is actually much louder then in windows but in very poor quality
I do NOT think it's b/z of the mp3...they are fine

what can I do ? do I need to install drivers ?

---

### Post by randytuggle on 2006-11-22
I've had distorted sound when I turn the master volume control UP to HIGH. If I turn the master volume to about 60% - and then use other volume controls (monitor volume, speaker knobs, etc), it works great. Have you tried adjusting the master volume? I'm a noob too - but I'd bet some people overlook this trick...

---

### Post by Delkster on 2006-11-22
> **randytuggle said:**
> If I turn the master volume to about 60% - and then use other volume controls (monitor volume, speaker knobs, etc), it works great. Have you tried adjusting the master volume? I'm a noob too - but I'd bet some people overlook this trick...

Actually, I've done exactly the opposite. I've noticed that, on my system, having the PCM volume control cranked all the way up can cause distorted sound, so I just keep that at about 80% of the maximum and use the other controls (namely Master) to adjust the volume when needed.

Maxddark, you may need to experiment a little on your system but if what you experience is distorted sound, it's probably worth a shot to try and lower some of the volume levels if they're set to 100%.

---

### Post by pandu.rs on 2006-11-22
I have creative 2.1 speakers. I once experienced similar problem when the audio jacks connecting to the computer and woofer were swapped..

so u could try swapping it.

(For me the jack in which it is written as sub must be connected to sub-woofer and the jack with a traingle in it must be connected to computer)

---

### Post by randytuggle on 2006-11-22
no subwoofer here. Just a HPv17 monitor with built-in speakers.

---

### Post by PrinceArithon on 2006-11-22
Make sure in your Alsa mixer you have the Master Mono turned up some as well.  If you have the subwoofers that controls them.  So if it sounds like your mp3's are playing from the inside of a coffee can, turn it up and see if that adds some bass to your songs.

---

### Post by imon9 on 2007-01-17
i am not 100% positive this can help, but there are few things you chould try out now:
(1) if you have gstreamer-fuendo-mp3 install, remove it, use gstreamer-bad instead (it show positive effect on many)

(2) update your ALSA driver to the latest (currently ALSA 14 RC2

(3) as for my case, uninstall your mixer native software and installing other one might help...for me, i have a Realtek AC 97 soundcard build-in with my twinhead laptop (nevermind if u never heard of it)...i tried ALSAmixer, xfce-mixer, gnome mixer but all somund bad, but when i changed to QAMix, all went to nice normal sound, go try your luck...

so i suggest QAMix for mixed, it is more compatible to ALSA setting architecture, i guess. Nice interface too. 

(4) For other who it didn;t solve it, try update your ALSA driver to the later ones (ALSA 14 RC2, at this moment) and use ALSA instead of OSS or other mechanism for playback... ESD is old sound driver, so it might be the cause of problem if ur machine use it as default
Edit/Delete Message

for your information:

my mic recoding is working fine too! i update ALSA and the mic start working flawlessly. Previously, with other mixer, my mic will be hard over my speaker ALL THE TIME no matter how i set to mute it. Now, it record my sound, but will not echo it over the speaker which is PERFECT.

btw, if this workes, please post a reply..and if it is not too much of trouble, please private massage me too...

i don't keep track where i answer these treads in the forums, but if this solve the problem, i want to write an article for the rest fo the ubuntu commmunity to know it... (and post it in the forum, in hope it can help others)

---

### Post by HomerSp on 2007-11-24
Sorry to bring up an old thread, but your solution worked perfectly for me. I have an on-board Realtek AC'97 card too, but before I did what you posted the sound really sucked (I am a big fan of music, so I want the sound to be perfect :P). 
Thanks a bunch :D

---

### Post by imon9 on 2007-11-24
hi HomerSp: 

you're welcome :) but some told me there is still cracking sound, so this solution might help if all else fail:

it is guide i posted last time on another thread:
[http://ubuntuforums.org/showpost.php...0&postcount=11](http://ubuntuforums.org/showpost.php...0&postcount=11)

---

### Post by Zackie on 2008-01-17
i have the new version of ALSA and i still have the same prob :(

---

### Post by Kenniej on 2008-03-15
Yappz , i came here for the same reason(sound cracking). I've lowerd PCM to about 75% and master at 100% and no cracking. 

So Whiii, good sound ^^

Grtz,
Kenniej

---

### Post by jamiedrilling on 2008-04-28
THANK YOU!  I just installed 8.4 and while I got wireless and my DVD player to work, the sound quality was awful.  Changing settings in the sound mixer was exactly what I needed to do and I confess - even though I'm steeped in Windows (I know, I know, I'm sorry!) and that would have been one of the first things I checked, with a Linux distribution I was concentrating on determining what sound card I had and whether the driver was right.

You fixed my last hassle with switching to Ubuntu Linux and I'm very grateful!

Jamie

---

### Post by blackb1rd on 2008-07-04
Yes, thank you very much, here indeed the same problem and lowered PCM to about 74, the alsamixer in console is set to db gain 0.0, I guess the problems occur when this number becomes positive (>74). Just like Jamie below, I was concentrating on other things and assuming the wrong driver or something had been auto-loaded :-)

---


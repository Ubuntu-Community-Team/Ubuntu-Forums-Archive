---
title: "Gusty Log off sound"
date: 2008-02-16
forum: Absolute Beginner Talk
---

### Post by Squid_blk on 2008-02-16
I first started with Ubuntu and Linux last year with Feisty and upgraded to Gusty when the update came out.  I did not change any of the settings concerning sound but my log off sound has not worked since the upgrade. The panel says to play the default sound but no sound happens when I shut down. It worked fine under Feisty but does not work with Gusty. Is there a fix for this? Thanks.

---

### Post by mgmiller on 2008-02-16
I was just about to post the same question.  

I noticed that not only the log off sound, but almost all the system sounds have stopped working.  

I used to get a nice click sound when I clicked one of the icons on my top panel, now it's silent.  The only system sound that still plays is the log on sound.  

If you go to System > Preferences > Sound and click on the sound tab, everything is checked off and enable system sounds is enabled.   
If I try the play button next to the selected sound, they all play fine, but in actual use, none of them work.

Sound in general works fine for all applications and players otherwise.

I assumed this was part of the interface regression in Gutsy, whereby they stopped using the splash screen and dropped other parts of the log on eye candy, and concentrated on compiz-fusion desktop stuff.

I am hoping it will be fixed in Hardy.
 If anyone out there knows a fix for Gutsy, please let us know.

---

### Post by thecure on 2008-02-16
> **Squid_blk said:**
> I first started with Ubuntu and Linux last year with Feisty and upgraded to Gusty when the update came out.  I did not change any of the settings concerning sound but my log off sound has not worked since the upgrade. The panel says to play the default sound but no sound happens when I shut down. It worked fine under Feisty but does not work with Gusty. Is there a fix for this? Thanks.

Greetings,
 
Sounds have worked fine for me in Gutsy and Hardy. Try opening up a terminal and typing "alsamixer"  (no quotes) Your sounds are probably muted. In alsamixer type "h" for help or just "F5" to show all your settings. This is especially useful if you have a mic that isn't working. Seems to be when ever a kernal upgrade sounds are muted by default. Incidentally arrow keys up/down to increase/decrease levels and "m" to mute/un-mute.

Hope this helps.

- Forget what I said, didn't read your question correctly. If you still have sound otherwise I'll need to research. Yes, I'm an idiot.

---

### Post by mgmiller on 2008-02-16
> - Forget what I said, didn't read your question correctly. If you still have sound otherwise I'll need to research. Yes, I'm an idiot.


:lolflag:

Yup, sound works fine in all apps., just no system sounds.

Please research.  I looked several times for many hours for answers to this and finally gave up.

:popcorn:

---

### Post by rainwalker on 2008-02-16
The same thing happened to me; Installing pulseaudio fixed everything

---

### Post by mgmiller on 2008-02-16
> The same thing happened to me; Installing pulseaudio fixed everything

I believe pulse audio is going to replace alsa in Hardy.

Was this as easy as:
```
sudo apt-get install pulseaudio
```

Or did you need to do something else?

---

### Post by rainwalker on 2008-02-16
The packages I have installed are:
libpulse0
pulseaudio
pulseaudio-module-gconf

---

### Post by mgmiller on 2008-02-16
When I looked just now, I already have libpulse0 installed for some reason, but not the other 2.  Maybe if I am feeling lucky I will try installing the other 2 and see what happens.

Did you need to do anything after installing these packages to get pulseaudio going, or did it just switch it over automatically and all was good?

---

### Post by Squid_blk on 2008-03-03
I tried the PulseAudio install and it has still not helped.  Any other suggestions?

---

### Post by crjackson on 2008-03-03
> **mgmiller said:**
> :lolflag:

Yup, sound works fine in all apps., just no system sounds.

Please research.  I looked several times for many hours for answers to this and finally gave up.

:popcorn:


+1 on 10 systems.  All started with a clean install.

---


---
title: "Problem with Audacity 1.26"
date: 2007-01-20
forum: Absolute Beginner Talk
---

### Post by SuperCool4678 on 2007-01-20
I'm running Kubuntu 6.10, and when I start Audacity, I get a message that says, 

"There was an error initializing the audio i/o layer.

You will not be able to play or record audio

Error: Host error."


I checked the Audacity forum, and a few other people reported this same problem.  Nobody has found a solution yet.

I use Audacity nearly every day for various things, and it would be nice to not have to switch back to Windows whenever I need to use it.

---

### Post by frotzed on 2007-01-21
That particular setting in Audacity is found in Edit > Preferences.  Unfortunately I can't help you more than that.  I'm using Ubuntu and Audacity works without a hitch for me but I've never tried Kubuntu.  Don't know why it would be different though.  I know it sounds goofy, but you've already tried rebooting, right?

---

### Post by The Mekon on 2007-01-22
I get this problem too if I try and use Audacity after using any other sound program.

If I use Audacity immediately after booting up Ubuntu it works OK and I am too lazy (probably dumb as well:)) to find out why.

Brian

---

### Post by SuperCool4678 on 2007-01-23
I tried using Audacity immediately after booting up and it does the same thing.

---

### Post by JustinAlf on 2007-01-25
I've used Audacity for almost a year.  As soon as I did an upgrade, it suddenly couldn't find my audio layer I/O  SO let me know if you find a sollution.  Beleive me, I've tried every possible sollution except for the right one!  please help someone

---

### Post by triwave on 2007-01-27
I have a similar problem. Somebody else suggested to try:

```
aoss audacity
```

Before I tried that I got the I/O error on start-up of audacity. After trying the aoss command Audacity starts without error but then gives the error when you try to play a file. I went to preferences and with the aoss command there are devices listed as /dev/dsp for both playing and recording (running audacity without aoss gives the error with no devices listed). They can't be changed to anything else and they apparently don't work.

Does that give any clues to anybody who might help figure out why sound does work?

---

### Post by Zimmer on 2007-01-27
[http://ubuntuguide.org/wiki/Ubuntu_E...rl](http://ubuntuguide.org/wiki/Ubuntu_E...rl) y_in_GNOME

The changes here to the esd.conf file are what sorted Audacity for me...  also, try disabling esd from the Preferences>Sound  and maybe disabling System Sounds and restarting...

---

### Post by triwave on 2007-02-01
Disabling ESD seemed to be the trick for me. Works fine now! Thanks :D

---

### Post by VraiChevalier on 2007-02-01
I got the same error message.

Then I read what The Mekon said and tried using Audacity right after reboot. It worked! 

Now to try some other stuff and see what happens....

---

### Post by Patrick K on 2007-02-01
I don't have any problems running Audacity except that the master volume and record level controls don't work. The track volume controls work but not the master or record level controls. Haven't and any luck on the Audacity forum (or here for that matter) except for suggestions to change distros.

---

### Post by SuperCool4678 on 2007-02-04
The thing that fixed this for me is going into the sound settings in "System Settings" and unchecking the "enable sound system" box.  This was suggested by someone on the Audacity help forums.

---


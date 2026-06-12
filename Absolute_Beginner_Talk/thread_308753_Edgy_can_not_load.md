---
title: "Edgy can not load"
date: 2006-11-28
forum: Absolute Beginner Talk
---

### Post by to4i on 2006-11-28
I installed TC Elite, and I have no sound in the game so I did
> sudo -s
echo "echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss" >> /etc/environment
echo "echo "et.x86 0 0 disable" > /proc/asound/card0/pcm0c/oss" >> /etc/environment
exit
But when I restarted, Edgy hang and could not load X. I had to remove the lines from the above file to boot up.
Any ideas.

---

### Post by to4i on 2006-11-28
up

---

### Post by drphilngood on 2006-11-28
Try troubleshooting with the [Comprehensive Sound Problem Solutions Guide v0.5e]("http://www.ubuntuforums.org/showthread.php?t=205449") and post back.

If you don´t have any luck, post back with your hardware specs and attach the pertinent parts of the following:

/var/log/Xorg.0.log

/var/log/syslog

/var/log/kern.log

and we´ll try to help get you sorted.

---

### Post by to4i on 2006-11-28
I do not have sound only in the game.
I tried Comprehensive Sound Problem Solutions Guide v0.5e and everything worked fine.

---

### Post by drphilngood on 2006-11-28
Did you start the game and make sure that all of its sound settings are correct and then experiment with your Alsa Mixer to make sure that nothing is muted or a level is too low, such as PCM or Analog Mix?  It might be worth double checking since you say all other sound is fine.

In addition, have a look [here]("http://www.truecombatelite.net/forum/viewtopic.php?t=5742&sid=dd2db97920d30cc6d6aab089c42dbcee").

> From that unofficial FAQ deely:

I'm having problems with sound - ie: no sound, or clashes with TeamSpeak.

This script, run with root privileges, should fix the most common cause of this. Alter to taste.

tceteamspeakfix.sh:

#!/bin/bash
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
echo "et.x86 0 0 disable" > /proc/asound/card0/pcm0c/oss



Notes for Ubuntu users:
(i)You will have to use sudo.
(ii)If you get funky access denied or permission denied messages, do these before trying again:
sudo chmod 666 /proc/asound/card0/pcm0p/oss && sudo chmod 666 /proc/asound/card0/pcm0c/oss

you can repeat that line with 644's instead of 666's to put permissions back after you've finished.

and here:

[Sound In Ubuntu. Or lack thereof.]("http://www.truecombatelite.net/forum/viewtopic.php?t=5715&sid=dd2db97920d30cc6d6aab089c42dbcee")

> Try killing any extraneous sound daemons, artsd for example.
```
sudo killall esd
```

---

### Post by to4i on 2006-11-29
I checked the sound settings and they are ok, nothing is muted.
> 
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
echo "et.x86 0 0 disable" > /proc/asound/card0/pcm0c/oss
Yes, this fixes the problem but till I restart the PC. When I save it to /etc/environment Edgy won't load X.(check my first post). How should I use tceteamspeakfix.sh file?

---

### Post by to4i on 2006-11-29
Ideas? :-k

---

### Post by drphilngood on 2006-11-29
Sorry I couldn´t be more helpful.  Perhaps one of the more knowledgeable members(hopefully, one that´s familiar with the tceteamspeakfix.sh file) will help get you sorted.

Good luck!

---

### Post by to4i on 2006-11-29
Ok, thanks for the help.
I hope somebody else will help..

---

### Post by drphilngood on 2006-11-29
You might get more responses if you either posted an aptly named thread in the [Gaming & Leisure section]("http://www.ubuntuforums.org/forumdisplay.php?f=93") or had this thread renamed and moved.:-k

---


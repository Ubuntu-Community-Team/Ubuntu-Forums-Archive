---
title: "no sound after update"
date: 2006-09-17
forum: Absolute Beginner Talk
---

### Post by Tucatts on 2006-09-17
OK third try. After the last big update last week that required a reboot I lost the sound. I have checked alsamixer and nothing is on mute. My nividia drivers seem to be fine and I can boot the system fine, in fact everything seems just dandy except NO SOUND! Ha Ha, that sounds like the cell phone TV commercial when the people scream (with no sound) "IT DROPPED MY CALL" Well, I kinda feel the same. So anyway any other suggestions other than re-install. I have the system running good and really do not want to reinstall again.
Thanks,
Tucatts

---

### Post by MerlinsLair on 2007-11-07
I have the same problem here too. Upon right clicking the volume icon then Volume Control I get the following error message:

No Volume Control GStreamer plugins and/or devices found

After checking...I find that they ARE installed.

Some help would be nice. Suggestions welcomed.

---

### Post by P4man on 2007-11-07
Ubuntu often seems confused about the different outputs. To enable my onboard sound, I had to move the slider "surround" all the way up. That slider is even hidden by default in the gnome mixer(you can enable it in preferences).

I'd suggest trying to  enable  ALL sliders, and move them ALL up,  for both ALSA and OSS (file > change device).

Merlins lair, google on that message. Many  results, like this one:
[https://answers.launchpad.net/ubuntu/+source/yelp/+question/8651](https://answers.launchpad.net/ubuntu/+source/yelp/+question/8651)

---

### Post by MerlinsLair on 2007-11-07
Thanks P4man, I'll give that a try and post back later on my results.

So far, no luck. Tried reinstalling the plugins, rebooted (no luck), checked to see that my username was included in the etc/group file (yes) so I'm still looking at this point for solution.

---


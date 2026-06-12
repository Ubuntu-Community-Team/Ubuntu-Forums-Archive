---
title: "MBP 6,2 with Oneric - No sound and wifi capped at ~12.5KB/s"
date: 2011-09-27
forum: Apple Hardware Users
---

### Post by swolliosis on 2011-09-27
My first problem is that I have no sound. I've tried all the gnome-alsamixer solutions of unmuting all the channels but it doesn't work. I even tried uninstalling the gnome-alsamixer package as well as simply running just the alsamixer through command line. Nothing works. I see the red LED in the headphone jack. The thing is, if i press the volume up or down button, it'll register it by making that volume sound once but after that, it's completely gone.

Edit: I've also tried the options snd-hda-intel model=mbp55 to /etc/modprobe.d/alsa-base.conf

Second problem: my wifi at my apartment (WPA2) is completely fine on but when I'm on my school campus internet (UT Austin WPA2 enterprise), my speed is slower than 56k and I can't figure out why it's so slow. I have my power plugged in and I even tried one of the desktop's ethernet cables but still the same. So it's not just the wifi I believe.

---

### Post by swolliosis on 2011-09-27
another thing: I logged in as a guest and the sound has no problems at all.... just on my username it doesn't work

---

### Post by swolliosis on 2011-09-27
okay... so I went back onto campus and my wifi started working.

and then i ran killall pulseaudio and my sound started working again.

does this mean that my pulseaudio is faulty and I'd have to reinstall it?

---

### Post by JJJ&amp;J on 2011-10-02
I'm actually here looking into how to install Oneiric on my MBP62, but with older version of Ubuntu, I had to unmute the speakers with alsamixergui or gnome-alsamixer (may be misspelled.) For reference, this had to be done only once after a fresh install.

sorry, missed you tried that already (dont know how, first thing you said!)

Odd. I'll check back after my attempt. It's hard to find info on exact OS/model, but seems to be important most times.

---

### Post by JJJ&amp;J on 2011-10-03
...well just installed Oneiric on this Macbook 6,2 (with Lion.) Audio works. Not even muted. This is the first boot after installing and surprisingly, no problems. I did use yesterdays Oneric daily live amd64+mac iso, installed from live session.

---

### Post by majortom67 on 2011-10-04
[https://help.ubuntu.com/community/MacBookPro6-2/Oneiric](https://help.ubuntu.com/community/MacBookPro6-2/Oneiric)

Also set analog output in system settings

---


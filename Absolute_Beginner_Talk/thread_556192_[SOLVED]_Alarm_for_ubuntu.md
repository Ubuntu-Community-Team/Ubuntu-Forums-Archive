---
title: "[SOLVED] Alarm for ubuntu?"
date: 2007-09-21
forum: Absolute Beginner Talk
---

### Post by ~~Tito~~ on 2007-09-21
Need an app that does this, my phone alarm and my ds lite isnt effective. Anytips? NEED ONE ASAP!! I need to wake up tommorow.

---

### Post by yabbadabbadont on 2007-09-21
:roll:

Go out and spend five dollars (or the equivalent where you live) for a battery powered (or wind up even) alarm clock.  Put it somewhere in your room that requires you to get out of bed in order to turn it off.

---

### Post by wheredidrealitygo on 2007-09-21
I use an xmms (music player) plugin called xmms-alarm.

works wonderfully, and i can wake up to any song I want. Hasn't failed at all yet (just test your speaker settings the night before)

make sure you leave xmms open, it can't open itself.

---

### Post by jordanmthomas on 2007-09-21
1.  find a loud song you can play.
2.  Make a file in your home directory name wakemeup and put this in it.
```
#/bin/bash
mplayer /path/to/music/file
```
3.  in a terminal,
```
chmod +x ~/wakemeup
```
4.
```
 crontab -e
```
Put this in there  (hit i to insert text, then esc when you're done...then press : followed by wq):
```
0 7 * * 1,2,3,4,5       /home/yourname/wakemeup
```

This will wake you up at 0 minutes past 7 hours on weekdays.
Make sure your speakers are on before you go to sleep.

The xmms-alarm seems easier though, so it's up to you.

**edit** you'll also have to listen to the whole song if you do it my way, or at least turn your speakers down.

---

### Post by ~~Tito~~ on 2007-09-21
Need an app that does this, my phone alarm and my ds lite isnt effective. Anytips? NEED ONE ASAP!! I need to wake up tomorrow.

---

### Post by bodhi.zazen on 2007-09-21
Threads merged.

---

### Post by wheredidrealitygo on 2007-09-21
two of us posted possible solutions above your last post.

---

### Post by wolfen69 on 2007-09-21
i found several in synaptic. such as kalarm. search for "alarm".

---

### Post by mocoloco on 2007-09-21
Two things to add to the great post by jordanmthomas related to using cron.  If you're not aware, cron runs scheduled tasks in Linux.  Firstly, if you want cron to be able to open any graphical app, you need to add a line to your crontab file.  In a terminal, do "crontab -e".  At the top of the file add this
```
DISPLAY=:0
```
Ctrl-X, Y <Enter> to save it.

There's a graphical tool to add cron jobs if you prefer,
```
sudo apt-get install gnome-schedule
```
Now you can put in a command like "totem <path to music file>", and you'll be able to close totem to shut off your "alarm".

---

### Post by ~~Tito~~ on 2007-09-21
opps, sorry for the double post. I went back to see the other threads similar but none had anything.

---

### Post by ~~Tito~~ on 2007-09-21
> **yabbadabbadont said:**
> :roll:

Go out and spend five dollars (or the equivalent where you live) for a battery powered (or wind up even) alarm clock.  Put it somewhere in your room that requires you to get out of bed in order to turn it off.

I have done that, but I am a dead sleeper, and a loud burst will wake me up not a on coming beep, like alarms are, because then I will be used to it by the time it gets loud.

xmms, huh? In synaptic?

---

### Post by jordanmthomas on 2007-09-21
You could also get an alarm clock with a radio.  Maybe it'd wake you up.

---

### Post by wheredidrealitygo on 2007-09-21
Yes, xmms, in synaptic.

xmms-alarm the plugin is also in synaptic.

---

### Post by ~~Tito~~ on 2007-09-21
Tried it, scared the crap out of me when I heard " HI WELCOME TO THE EARLY NEWS WITH TOM AND JANET, TODAYS WEATHER IS CLOUDY WITH A SLIGHT CHANCE OF RAIN!!! OK TOM NOW WE ARE HITTING UP SOME COUNTRY TUNES!!!". Thats exactly how it went, then I chucked the thing across my room. This was a few days ago. I would rather listen to something I like XD. :lolflag::lolflag: 

Thanks guys I just got it configured, how will it go off? It doesn't have a tray Icon? I have a laptop and I don't have anything happen when I close it so it will be fine and I have a cpu cooler under it so I'm fine, just worried it exits and you would have to leave it running all night with the little window on.(My screen turns off when I close it so it wont do any damage, just wondering if it will come on :).)

---

### Post by ~~Tito~~ on 2007-09-21
> **wheredidrealitygo said:**
> Yes, xmms, in synaptic.

xmms-alarm the plugin is also in synaptic.

Yea, I did a search for that and it was pre installed, I searched for xmms-alarm and It installed all the plugins with xmms.

---

### Post by jordanmthomas on 2007-09-21
You can try it out by setting it for about 5 minutes in the future and making sure it works as advertised.  If it does, then you can change the time for in the morning and you'll be goo[SIZE="7"]**D**[/SIZE] to go.

---

### Post by ~~Tito~~ on 2007-09-21
"goof to go?" XD, no I know what you mean ;).

EDIT:IT WORKS!!!!

---

### Post by wheredidrealitygo on 2007-09-21
If you'd like to put it in the system tray, there's an AWESOME (I can't stand being on a computer without it) application (also in repositories) called alltray.

launch it, click any application window, and it instantly makes a system tray icon for it (and minimizes it to said tray icon).

you can click the tray icon to bring up the window, and click the tray icon again to minimize back to tray. also can undock it. note: doesn't work properly with compiz-fusion yet.

---


---
title: "Stopping mplayer started by cron"
date: 2006-10-11
forum: Absolute Beginner Talk
---

### Post by Boatswain on 2006-10-11
So I went and made myself an alarmclock by following the directions [here]("http://grimthing.com/archives/2004/01/23/cron-mp3-alarm-clock/"), and I'm quite satisfied with it.  The only problem is, I put about 20 sonds in the playlist, and once it starts I don't know how to make it stop, since mplayer doesn't come up.  What am I missing?

Thanks!

Tom

---

### Post by jordanmthomas on 2006-10-11
you could type
```
killall mplayer
```
in a terminal.

Not elegant, but would gain you some serenity.  :)

---

### Post by mssever on 2006-10-11
The simple solution would be to type killall mplayer. This would backfire if you had another instance of mplayer running that you wanted to keep. In that case, you'd need to get the pid of the alarm instance (either through some script/pidfile means or through ps-ef | grep mplayer) and type kill <mplayer pid>

---

### Post by Boatswain on 2006-10-11
Hey thanks!  Now I won't be forced to listen to those chill wake-up tunes all morning.

Tom

---


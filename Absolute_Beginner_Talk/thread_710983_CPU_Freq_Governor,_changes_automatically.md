---
title: "CPU Freq Governor, changes automatically"
date: 2008-02-29
forum: Absolute Beginner Talk
---

### Post by karlo on 2008-02-29
Normally, my default setting when my laptop is on AC Mode, is OnDemand, which avoids any over heating even though it's plugged in and of course,  I would not like my hard drive's life to be heated as long as my laptop is ON, so OnDemand will just increase the speed if needed.

On my battery, I use conservative.

Weird, after browsing or watching a movie, the frequency is always in the maximum state, 1.70GHz, never goes down.

When I checked it, I am using the Performance Governor! How did it happened? I am using OnDemand by default...

I changed it to OnDemand, after a minute, still the frequency does not goes down, it converts to Performance.

---

### Post by Rocket2DMn on 2008-02-29
I've had this problem myself, although it didn't change to performance in GConf Editor, but it did stick at the highest CPU freq.  I'm not sure if it's a display glitch or if the frequency is actually stuck there.  You can try restarting X to see if it's fixed (then it's probably a display glitch), otherwise you just have to restart.  Maybe you'd like to file a bug report for us :)

---


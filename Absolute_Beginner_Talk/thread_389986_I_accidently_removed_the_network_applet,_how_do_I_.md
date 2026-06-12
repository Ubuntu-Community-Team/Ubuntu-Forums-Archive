---
title: "I accidently removed the network applet, how do I get it back"
date: 2007-03-21
forum: Absolute Beginner Talk
---

### Post by monkeyking on 2007-03-21
Well the nice icon with the bars next to the time and date.
How do I get it back

thanks in advance

---

### Post by dracomordag on 2007-03-21
right click the bar, hit "add to panel", something resembling network status or something should be an option

---

### Post by lamalex on 2007-03-21
you cry and do a fresh install. That's the only method ive found that works. i've tried em all. it's really sad :( network-manager is so insignificant for a fresh install, but it's so important uggghh i've been really careful not to remove mine this time.

---

### Post by charles.g.moore on 2007-03-21
Do you still have a connection?
Do you mean that you right clicked the bars and clicked quit?
Is it still on your system?
Can you try alt-F2 nm-applet
Can you hard wire into your router and then do an sudo aptitude install nm-applet?

---

### Post by charles.g.moore on 2007-03-21
> **monkeyking said:**
> Well the nice icon with the bars next to the time and date.
How do I get it back

thanks in advance

I did some searching and found this:
[http://ubuntuforums.org/showthread.php?t=242700](http://ubuntuforums.org/showthread.php?t=242700)

---

### Post by monkeyking on 2007-03-21
Well,
I actually got it back.
---------------------------------------------------
It was quite simple,
I right clicked on the bar, chose add to panel,
and added network-monitor.
After that I just had to tell that I wanted to monitor my ath0 connection.
---------------------------------------------------
I'm using edgy, and all the forum pages about this were taking about nm-applet.
This is a kind of puzzeling, since network-monitor is not the same as nm-applet.
----------------------------------------------------
The reason why I started mezzing around with this,
was that I wanted to do a vpn connection,
and then another forum post was talking about how easy this was with nm-applet.

So I installed nm-applet, and these 2 applets look completely alike.
But the nm-applet doesn't seem to understand that my network workd.

---

### Post by dracomordag on 2007-03-21
good to see it all worked out!

---

### Post by t4thfavor on 2007-03-21
I removed the one that tells you that there are updates, the network status, and the battery status. Its simple to get it back, All you have to do is right click the panel, pick add to panel, scroll to the bottom and pick a notification area. That will put it back just how it was.

---

### Post by charles.g.moore on 2007-03-21
I did not even think about the different app thing, just goes to show how ego-centric I am.  I automatically assumed you must have the same setup as I have (haha)
Well, good to know you figured it out...

---

### Post by bakermiller on 2007-05-12
> **Iamalex said:**
> you cry and do a fresh install. That's the only method ive found that works. i've tried em all. it's really sad :( network-manager is so insignificant for a fresh install, but it's so important uggghh i've been really careful not to remove mine this time.

man!!! You got me freaked!!! 

- - - - - - - - -

All i had to do was add "notification area"  (actually nm-applet i guess(!?)).
 i found that on another thread about this issue. [http://ubuntuforums.org/showthread.php?p=2644524#post2644524](http://ubuntuforums.org/showthread.php?p=2644524#post2644524).

i can now see my network in the panel again.

thanks for the thrill!!

---


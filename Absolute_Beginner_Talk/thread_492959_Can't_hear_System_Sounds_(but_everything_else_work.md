---
title: "Can't hear System Sounds (but everything else works!)"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by EvilMarshmallow on 2007-07-05
Hey all,

I just did a fresh install of Feisty.  On the liveCD, I could press buttons for system sounds and they'd work.

Once installed to the hard drive, all sound works.  If I open a music file, I can hear it, in good quality.  If I open the sound files for system sounds manually (via nautilus) everything's good.  But when I assign a sound to any of the "system sounds" fields and press "test", I get... silence.

I have onboard sound as well as a Sound Blaster Audigy LS.  No amount of fiddling with settings has accomplished anything.  Right now all my other sound is directed out of the Audigy, and it sounds great... but why aren't system sounds working?

---

### Post by orb9220 on 2007-07-05
[http://www.ubuntuforums.org/showthread.php?t=205449&highlight=sound](http://www.ubuntuforums.org/showthread.php?t=205449&highlight=sound)

---

### Post by EvilMarshmallow on 2007-07-05
Been through that already, thanks...  

That guide assumes that you can't hear anything... which isn't my problem.

**I can hear sounds**.  I have the driver loaded.  It ***WORKS* for all music players **and stuff... I just can't hear the System Sounds for items like login/logout.

---

### Post by davidshere on 2007-11-17
I also have this problem.  I can hear sound great from Rhythmbox, etc.  But no system sounds.  The problem gets more interesting when I discover that the system sounds work fine in some logins but not others.  I decided to try to follow the tutorial listed above.   Several problems.

When I type
```
lspci -v

```
I get a very long response, and I *think* that this is the relevant information:
```
00:0d.0 Multimedia audio controller: Ensoniq ES1370 [AudioPCI] (rev 01)
        Subsystem: Unknown device 4942:4c4c
        Flags: bus master, slow devsel, latency 64, IRQ 5
        I/O ports at d800 [size=64]

```

The link that it gives for the sound card drivers,  [http://www.alsa-project.org/alsa-doc/]("http://www.alsa-project.org/alsa-doc/") doesn't work.  

Step (3) says:  "try to match the chipset you found in step 2" but step 2 doesn't say anything about finding chipsets.

Since I'm not sure if I got the right information from Step 2, and I'm not able to do Step 3, I probably shouldn't go on, but I do anyway.

In Step 4, when I type 
```
sudo modprobe snd-
```
and then type the tab key, my computer beeps and nothing else happens.

I could go on, but I decided to give up at this point. 

Maybe now that it's about 2 years later, there's a better tutorial somewhere or a bug somewhere has been fixed.

---


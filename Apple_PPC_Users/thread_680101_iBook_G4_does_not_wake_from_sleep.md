---
title: "iBook G4 does not wake from sleep"
date: 2008-01-27
forum: Apple PPC Users
---

### Post by Wizzel on 2008-01-27
I have been researching a fix for the computer not waking from sleep after the lid is closed. Most threads are just filled with replies with people from the same problem. I found one thread with a possible fix but it is dated 2005 and I am hesitant to try it. Let me know what you guys think. Again, I am not a pro with Ubuntu so please explain in detail what I should do. Thanks.

---

### Post by Wizzel on 2008-02-02
Anyone have a clue? This issue is very annoying.

---

### Post by stream303 on 2008-02-02
Unfortunately, it's quite a legendary problem, not only for ppc, but for PC's as well.  I wish I had a quick answer.  I have the same problem on an HP tablet pc.

Check out the following thread in the PC forums, with 25,000 views as of this writing:
[http://ubuntuforums.org/showthread.php?t=588239](http://ubuntuforums.org/showthread.php?t=588239)

Until we find an answer, can you get hibernate to work?

---

### Post by Gen2ly on 2008-02-02
Yes, I think this is the same problem I got ( I have PPC though ).  Gnome Power Manager has this issues listed a long time.  If you looked at the Gnome Power Manager buzilla you'll see ton and tons of reports so, it's not very likely this thing will be fixed anytime soon.  You should be able though to use the HAL switch to set PMU to sleep:

```
sudo /usr/libexec/hal-system-power-pmu sleep
```

---

### Post by stream303 on 2008-02-02
Dirk, that's promising!

I'm running Feisty on my 20" G5 iMac, and had to use "locate hal-system-pmu" to find it.  On my system, it shows up in:

/usr/lib/hal

I ran as root the command /usr/lib/hal/hal-system-power-pmu  sleep

but it always responds with "failed to open /dev/pmu"

Maybe it's my specific iMac?

I can see putting this into a little shell-script or gnome run menu.....  So close! :)

---

### Post by stream303 on 2008-02-02
Ok,, so I tried resetting my pmu just in case.

Holding down cmd-option-p-r while pushing the power button and waiting for the beep was a lesson in manual dexterity on the Imac. :lolflag:

But still the command fails with "failed to open /dev/pmu".

Ok, gotta' research this one.  However this might work wonders for some other machines!

Thanks for the tip on where to look!  I'll report back as soon as I find it....

Update:  I see in the Ubuntu bug reports that Benjamin H. is involved!  And I thought he only hung out in Debian.  Good to see Ubuntu and upstream working together....

---


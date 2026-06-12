---
title: "Berserk Tecra 8200 - hidden process?"
date: 2008-02-06
forum: Absolute Beginner Talk
---

### Post by kanketsu on 2008-02-06
Hello all, just installed 7.10 on my ol' Tecra 8200. Although the pre-installation wasn't exactly a walk in the park - having not reaching the live environment but was met with half BSOD instead for several times - it seems up and running just fine now. 

One concern, though. The fan now blows all the time, indicating that the processor was doing something all the time, too. I believe the next logical thing was checking the system monitor, so I checked that.

The number next to "CPU" was fluctuating between 90-96%. I'm not sure what it meant ... but i think it is safe to assume that it says 90% CPU was taxed at that moment, hence the fan blowing.

So I checked the "Processes" hoping to find the culprit. :)
But none of the processes listed there, except for the system monitor itself, was running. Everything was listed at 0%.

Any ideas what process should I turn off? Or does it mean that the Tecra is too old for running 7.10? It runs WinXP just fine, not "berserked" like this 
:guitar:

Oh, and I should mention that there isn't any visual enhancement selected at the moment. In fact, the interface looks kinda duller than when it runs XP, as if it's not the correct resolution or 16 bit instead of 32.:confused:

Thank you.

---

### Post by viciouslime on 2008-02-06
When you're on the processes tab, click view/all processes to see system processes as well. Then you'll be able to tell what is causing you this issue. Post back with what it is and hopefully someone will be able to help you :)

---

### Post by kanketsu on 2008-02-06
Will do. Thanks for the tip!

---

### Post by kanketsu on 2008-02-07
This is weird.

I didn't touch the lappie for two days, and when I turned it on this morning, it was suddenly normal: CPU load was listed around 10-20%. No fans blowing mad.

... :confused:

It should be noted, though, that the fan still kicks in quite frequently, (almost) as frequent as under XP. Well, I was under the impression that Ubuntu is lighter than XP, perhaps close to or even lighter than Win 2000 so the old Tecra doesn't have to do some heavy lifting anymore.. I haven't even installed Bit Torrent client yet.

Should I abandon Ubuntu and get Xubuntu instead? I'm considering it, but a bit hesitant since its blue interface looks rather, uh, ... bland. On the other hand, the current Ubuntu installation doesn't let me to turn desktop effects on, so perhaps I won't be missing any visual treats by switching to Xubuntu? :D

---

### Post by jordanmthomas on 2008-02-07
The program eating all your cpu up at first was likely trackerd, which indexes your hard drive to make it easy to search.

Also, in my experience, Ubuntu is NOT light any more.  Maybe back a year or two ago, but now they include too much stuff.  

As for you not wanting to use xfce because it's bland and blue, you can use the same themes in xfce that you can use in gnome.

Lastly, 10-20% CPU is still a little high.  Mine idles at 0%-1%, and that's with a script running that calculates a bunch of system information once a second.
Perhaps your graphics drivers aren't set up right?

---

### Post by kanketsu on 2008-02-07
It's the one under System>Administration>Screens and Graphics, right?

There's only one option for Trident under Choose Driver by Name, and only one Cyberblade under by Model, so I believe I have set it up right. At least that's what I thought. But the icons do look bland/ simplified (jpeg files seems to be okay, I think), so I can't be too sure :D

Perhaps it reaches 20% because T8200 simply belongs to the Stone Age? Although I don't want to think it that way :D

---

### Post by jordanmthomas on 2008-02-07
:)  Perhaps, but my CPU usually only runs at 600 MHz and still the utilization is low.
My graphics (integrated intel) does have pretty good drivers though, yours may not (and I'm pretty sure the Trident drivers won't work with compiz, which is why your desktop effects won't work).  This is probably the cause for the added CPU usage.

What do you mean by bland icons?

---

### Post by kanketsu on 2008-02-07
I'll try to describe it the best I can. It looks like there were only thousands of colors, not millions. I could be wrong in assuming so, perhaps because almost all icons in Gnome are this orange-brownish with minimal of shading, giving an unanimous feel, yet rather bland. I'm not sure if this is the way Gnome should look, or if there is something wrong with my system.

Or it's probably the simple fact that the old Tecra is sitting nicely on my desk, right next to a Macbook...  :lol:

Oh, BTW, is there an option like "Use small icons"?

---

### Post by kanketsu on 2008-02-17
Hmm.. after observing it for several days, it looks like the washed-out-colors were, probably, mostly related to the machine being old. It simply has lower technical limitation than the current machines.

But yeah, the Macbook seems to be the culprit. Must be it. :lolflag:

---


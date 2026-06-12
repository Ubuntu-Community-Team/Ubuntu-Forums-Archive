---
title: "Why do things just &quot;stop working&quot; in Ubuntu/Linux?"
date: 2008-03-26
forum: Absolute Beginner Talk
---

### Post by Patto77 on 2008-03-26
I've been using Gutsy KDE/Gnome for the last couple of months now, and I'm becoming curious and a little frustrated as to why things suddenly stop working.  

Just a few examples:

The taskbar suddenly 'disappears' forcing me to go into kcontrol and reset it.

Icons disappearing from the taskbar, only to miraculously reappear.  Ktorrent and Kmix are two regulars.  

Menu items across all applications sometimes just 'disappear'

Most of the time Emerald loads. Sometimes it just 'doesn't'. A restart or a terminal fixes it, but it's inconsistent.

Bluetooth occasionally ceases to function.  Sometimes it comes back, sometimes it doesn't.

Applications that are started, but you can't access them ie Ktorrent, Amorak.  Sometimes killing the processes help. 

The above examples are just a few I've noticed in the last couple of days.  I can understand things going wrong after an update or such, but I haven't actually updated anything.  Sometimes things go strange after a a restart.  Other times they happen in a 'stable' session.  It's the inconsistency and broad quirkiness that annoys and perplexes me.

Basically, why does Linux inexplicably stop working?  I know it's a BROAD question, but quite frankly, I don't where to begin.  Any general pointers-explanations appreciated.

---

### Post by penguinpi.com on 2008-03-26
For the most part things just don't "stop working" unless you do something or there is some type of hardware incompatibility. What type of hardware are you using (brand, processor, etc)?

---

### Post by Junglizer on 2008-03-26
This is b/c a lot of things that are released in linux as "working" are sort of cobbled together. Now I'm not saying this is the case with all of the issues that you've mentioned but this is a good way to describe wireless in linux. Hardware can be so very different. So what works 99/100 times may be released or at least be considered the way to get something working. Then you just might be the (un) lucky 1/100.

---

### Post by northern lights on 2008-03-26
I'm sorry mate, but I gotta agree with the penguin to the fullest -

nothing will simply seize working after a while.

If you're doing it for the first time, or with brand new hardware, Linux might be a bit of a bitch to configure, but once it's up and running it's generally very stable.

I'm not saying you're making your problems up - obviously weird things are happening in your OS - but you've said it yourself, your question is broad as f*ck! Could you post some specs and maybe a few screenshots of what's happening?

By your so far vague descriptions, I'd say it's a graphics issue, likely only happening with emerald/compiz. Not a long-term solution, but if it starts screwing up and you have important work/data that needs to be saved, run ```
metacity --replace
``` and your menu's etc might just come back...

---

### Post by drbob07 on 2008-03-26
> **northern lights said:**
> 
By your so far vague descriptions, I'd say it's a graphics issue, likely only happening with emerald/compiz. Not a long-term solution, but if it starts screwing up and you have important work/data that needs to be saved, run ```
metacity --replace
``` and your menu's etc might just come back...

He says he has to go into kcontrol to reset it
> forcing me to go into kcontrol and reset it.


So wouldn't it be
```

kwin --replace

```
Instead?

---

### Post by Trail on 2008-03-26
OP: Are you sure it's not any systray/multiple desktop confusion?

And if you using KDE and have taskbar issues, maybe it's compiz. Try taskbar-compiz (and pager-compiz) if that's the case.

---

### Post by northern lights on 2008-03-26
Yep - if he's indeed running KDE you'd be right. Shoulda read more carefully - good point.

---

### Post by Patto77 on 2008-03-26
> **northern lights said:**
> I'm sorry mate, but I gotta agree with the penguin to the fullest -

nothing will simply seize working after a while.

If you're doing it for the first time, or with brand new hardware, Linux might be a bit of a bitch to configure, but once it's up and running it's generally very stable.


But that's just it, somethings do just stop working.  Another example is while in VLC watching an avi, pressing the space bar pauses/unpauses.  It works fine for X amount of presses then one press to a many, 'bam' it no longer works.  That's the sort of 'simply sieze working' I'm alluding to.

The install is only a couple of weeks old and is most likely still in the 'bitch to configure' stage.

Specs:
Pentium D 2.8
1.5 Gig ram
7600gs 512 169.07

Ultimate Edition Distro of 7.10 Gutsy with both KDE and Gnome desktops/apps.  A Frankenstein version I guess.    Most of these problems have been whilst in a KDE 3.5.8 session.  So a compiz/graphic problem is more than the likely culprit.

In terminal usage, I'm still in the dark as to all the commands.  It doesn't help that there appears to be at least ten different ways to do the same thing at times. :)

---

### Post by northern lights on 2008-03-26
The "Ultimate Edition" is not a Canonical release but a community supported version (comes with more/other software). I've never used it and I don't wanna say it's bad at all - it might just be an idea to try an original release instead, since you're obviously having a load of trouble.

[EDIT]

Scratch that maybe -

the 7600GS is known to be a troublesome card. Have you tried [Envy]("http://www.albertomilone.com/nvidia_scripts1.html")?

[/EDIT]

---

### Post by Patto77 on 2008-03-26
I  had the Gnome original release of Gutsy first, but actually had even more hassles with that install.  I was keen to try KDE so opted for the ultimate edition 1.7.  As far as I can tell, it's just Gutsy with two desktops with a lot more apps added.

As for having a troublesome 7600, It's always nice to know your components are the hassle worthy ones ;)

 I haven't tried Envy, I might look into it.


Thanks for the replies.

---


---
title: "Logout problems"
date: 2008-01-28
forum: Absolute Beginner Talk
---

### Post by mech7 on 2008-01-28
Whenever i logout the system hangs at my wallpaper.. if i then press the power button it does turn off after a long time..

Does anybody know what could be wrong ? Also when i shutdown i get a big text in red saying System is shutting down ?

---

### Post by nemilar on 2008-01-28
Sounds like there's a process hanging when you're logging out.  You can try switching to a TTY (usually control+alt+Function key, so for example Cntrl+Alt+F3), logging in, and running ```
top
```

You might see some program eating up resources.  You could also try watching other processes as they exit, and see if there are any left stranded; once you figure out what processes it is that isn't quitting correctly, it'll be easier to solve the problem.

As for the "System shutting down" message, this sounds normal.  Linux is a multi-user OS, so when it shuts down, it sends a message to everyone on the system that the machine is shutting down.

---

### Post by MaximB on 2008-01-28
Actually I have a similar problem when I try to Logout.
It just hangs and I can do nothing , no terminal switching to x restarting only pushing the restart button.

---

### Post by nowshining on 2008-01-28
there is a problem in gutsy where pressing the logout button will freeze the system for 1m - known and won't get fixed in gutsy - look at my site in my sig for a workaround.

---

### Post by MaximB on 2008-01-28
Thanks I'll try it on my next restart...

---

### Post by nowshining on 2008-01-29
kool tell me how it works out - :)

---

### Post by megamanwich on 2008-02-02
I have a similar (same perhaps?) problem to MaximB. I can shutdown and restart normally, but if I choose the logout option my computer hangs at a blank desktop background (no mouse pointer). Not able to ctrl-alt-backspace or switch terminals. Restarting X doesn't work outside of the logout freeze either.  I have tried nowshining's solution to no avail (thanks anyways though).

edit. ctrl-alt-delete will restart my computer when I'm stuck at the desktop background bit.

---

### Post by MaximB on 2008-02-05
> **nowshining said:**
> kool tell me how it works out - :)

Nop it doesn't work for me.

---

### Post by MaximB on 2008-02-05
> **megamanwich said:**
> I have a similar (same perhaps?) problem to MaximB. I can shutdown and restart normally, but if I choose the logout option my computer hangs at a blank desktop background (no mouse pointer). Not able to ctrl-alt-backspace or switch terminals. Restarting X doesn't work outside of the logout freeze either.  I have tried nowshining's solution to no avail (thanks anyways though).

edit. ctrl-alt-delete will restart my computer when I'm stuck at the desktop background bit.

What video card you have ?

---

### Post by gfxguy on 2008-02-06
I have the same problem, it's not video card because I have several different accounts, and only one has the problem.

I'm sure it's some simple configuration, as it's my main account (and so it's the oldest, been around through many upgrades).

I'm wondering if there's an easy way to just start over with a fresh gnome session... which directory's could I possibly remove/rename and just copy over the default setup created when a new user is created.

---

### Post by lawina on 2008-02-10
I am having this problem too.

---

### Post by chadjohnson on 2008-02-16
Me too.

Gutsy has given me nothing but grief.

---

### Post by nilarimogard on 2008-02-18
I'm having the same problem. Did anyone find a solution?

---

### Post by Phristen on 2008-02-18
Sign me up too :confused:
Good thing Hardy isn't too far away.

---

### Post by CFath on 2008-02-18
I also have the shutdown/restart problem.  It has just started doing this and I don't know why.  It does it in every situation.  I have to shut down by holding the start button.  Hopefully someone can fix this soon!

---

### Post by Phristen on 2008-02-18
Well guess what, I found a fix :)
It seems to be an issue with ATi driver, but after I installed the latest 8.02 it went away.

---

### Post by mech7 on 2008-02-19
Yup latest driver works :D it still does not resume from hibernation correctly btw..

---

### Post by gfxguy on 2008-02-20
It's NOT a video driver issue... first, I have Nvidia; second, only one of the accounts on the box has the problem.

---

### Post by nilarimogard on 2008-02-21
Mine was also fixed after i upgraded to 8.02 so that must be it!

---

### Post by gfxguy on 2008-02-22
> **CFath said:**
> I also have the shutdown/restart problem.  It has just started doing this and I don't know why.  It does it in every situation.  I have to shut down by holding the start button.  Hopefully someone can fix this soon!

Try control-alt-backspace, first.  I can get to the login screen and shutdown from there.

---

### Post by petrolheadjman on 2008-05-05
hay guys i have the same problem,
been having it since like 7.04. 
Im on ubuntu 8.04 now and i have a different video card so i dont know why it is happening now. 
I have a nvidia 8600gt btw

if anyone can help that would be great

---

### Post by gfxguy on 2008-06-04
I just wanted to add to this thread; I don't think the problem's been resolved.  For me it absolutely was not a video card issue... most accounts on my box simply did not have the problem.

I actually rebuilt the account that did (the oldest one, which had been through the most upgrades), and the problem went away... it's something IN the account settings, probably somewhere in the .gnome2 hierarchy or something.

---


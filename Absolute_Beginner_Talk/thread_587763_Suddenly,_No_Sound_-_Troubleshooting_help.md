---
title: "Suddenly, No Sound - Troubleshooting help?"
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by hyper7 on 2007-10-23
I haven't done anything recently other than changing from a DSL modem to a wireless router, and now I have no sound.

Linux ran fschk when I rebooted, after messing around in XP, and I've had no sound since.  

When I check the sound settings, they all seem to be correct, but the system will freeze when I set the ALSA driver and try to test it.

Other than reinstalling sound drivers, I'm clueless as to what to do in order to troubleshoot the problem.  The only thing that's changed is how my NIC connects to the internet(which I see as an unrelated issue).

Any help would be appreciated.

---

### Post by hyper7 on 2007-10-23
Also, I noticed that flash videos were only playing for a few seconds at a time.

I booted into an older kernel, thinking that may do something, but to no avail.

I've read all the sound problem threads which relate to gutsy, yet I've not found one which resolves the problem I'm experiencing. =/

I guess I may be looking at a fresh install.

This is, indeed, very strange.  My SB Live 5.1 card is detected just fine, yet ALSA doesn't seem to be treating it properly.... all this after doing nothing more than changing from a DSL modem to a wifi router and running fschk.

Spose it's nice to have these things happen to me every now and then so that I continually keep backups and also stay familiar with the fact that nothing -just works-.

---

### Post by Sef on 2007-10-23
> I haven't done anything recently other than changing from a DSL modem to a wireless router, and now I have no sound.

Is there a way to check it on a wired router to see if the sound plays?

---

### Post by hyper7 on 2007-10-23
> **Sef said:**
> Is there a way to check it on a wired router to see if the sound plays?

of course.

i'll try that now.

---

### Post by hyper7 on 2007-10-23
And I have sound again, but I'm not connected to my wireless router.  I should have clarified this earlier.  I _was_ directly connected to a d-link wireless router.  I was using the wifi capabilites for my PSP.

So what I've done thus far is to disconnect my NIC from the d-link and plug it back into my westell 6100 DSL modem/router(it is both a router and a modem).

Now that my NIC is plugged back into the DSL modem, I have sound.  I'm sure you can figure what'll happen if I switch back to the d-link wireless router.

Is there any way to resolve this?  I'm _very_ clueless at this point.

Your help is _always_ much appreciated..

---

### Post by hyper7 on 2007-10-23
I'm willing to do some tests and break my gutsy in order to find out the problem.

To me, this doesn't make much sense, but this is what happens.

I'm trying to think of what the difference may be from being connected to my router and connected to the dsl modem directly.  As far as I know, linux should be handling packets the same way.  The only major difference is that maybe my router is now working as a switch.  I don't understand why that would affect the sound card.

Also, I do have an onboard NIC that I don't use( I use an old 3com), but I have that available but disabled via BIOS.


To me, it seems like a kernel problem, but I can't figure out why the kernel would kill my sound card(not on board).

There's nothing important to me that I can lose, so I'll try whatever in order to fix the problem or at least diagnose it.

Thanks

---

### Post by sciencectn on 2008-01-14
Try live booting Ubuntu and see if the sound works. If it does, connect to your router on the live boot, and test it again.

---


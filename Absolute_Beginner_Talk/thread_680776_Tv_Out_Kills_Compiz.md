---
title: "Tv Out Kills Compiz?????"
date: 2008-01-28
forum: Absolute Beginner Talk
---

### Post by bagrol1 on 2008-01-28
I used the graphical interphase to set up my LCD and monitor as follows:

LCD (main) 1680x1050 60Hz
Monitor (TV): Plug and Play 640x480 60 Hz extend to the right.

This works and I can get some live stream video sent to the TV. And this is the only configuration which works.

However, after doing this setup compiz is dead and I can only use the default setup with no visual effects.

I have NVIDIA 7900GS and use the latest NVIDIA video driver.

What is at fault here:

a) Compiz not compatible?
b) video driver not up to par?
c) setup???

Should I set the xorg.conf manually (how?) to make it all work or there is some other utility like RANDR to try? 

Who could help? Somebody at Canonical? Is there a official support source I could ask? I tried filing a bug before but received no official response, just some user responses confirming the bug (something different).

Thanx!

---

### Post by bagrol1 on 2008-01-28
Anybody? No experience with Compiz and TV out and NVIDIA cards on Gutsy????

---

### Post by emarkd on 2008-01-28
No experience with that but Canonical does offer [paid support]("http://canonical.com/services/support") if you're interested.  However, remember that Compiz is beta software so you'll probably get no help from them either.

Have you tried posting at the [Compiz forums]("http://forum.compiz-fusion.org/")?

---

### Post by sloggerkhan on 2008-01-28
Well, what happens when you try to run compiz? Is there any console output?

I know I've seen compiz functioning on multi-monitor setup with nvida cards in videos.

---

### Post by bagrol1 on 2008-01-28
The screen flickers, goes black for a second and then a message is displayed that special effects could not be used.

> **sloggerkhan said:**
> Well, what happens when you try to run compiz? Is there any console output?

I know I've seen compiz functioning on multi-monitor setup with nvida cards in videos.

---

### Post by sloggerkhan on 2008-01-28
I don't know my way around nvidia cards (I have an ATI), but you are using the proprietary driver, I am assuming?

---


---
title: "recent hardy update breaks intel driver?"
date: 2009-02-15
forum: Apple Hardware Users
---

### Post by gonr on 2009-02-15
I have a macbook with the GMA X3100 graphics card, in Hardy. Everything was working fine until a package update I did yesterday. Now, if I try to play any movies using totem or mplayer, x locks up and I have to reboot the computer. 

I get errors in my X logs that other people used to have with the intel drivers but which where apparently resolved. I get various errors like:
(WW) intel(0): ESR is 0x00000010, page table error
(WW) intel(0): Existing errors found in hardware state

or, another time:
Error in I830WaitLpRing(), timeout for 2 seconds
Fatal server error: lockup


I tried reverting a few of the packages that were updated, that seemed like they might have to do with it, but this had no effect.

I've attached the list of updated packages, as well as two X.org logs (which I had to compress for the forum).

Has anyone else seen this? Is there something simple I can do to revert to the state the computer was in before yesterday?

---

### Post by gonr on 2009-02-15
hmmm... it seems to be fixed now, I think after I suspended+awakened.

It's strange that restarting had no effect, but suspending did.

---

### Post by cyberdork33 on 2009-02-15
> **gonr said:**
> hmmm... it seems to be fixed now, I think after I suspended+awakened.

It's strange that restarting had no effect, but suspending did.
several pieces of hardware in a mac are not reinitialized on a reboot. You have to actually completely powerdown and startup again. suspending would of course powerdown and restart the graphics card...

---


---
title: "Kernel Panic"
date: 2008-01-19
forum: Absolute Beginner Talk
---

### Post by Squizz on 2008-01-19
When I try to boot, or runthe live CD then I get the error message 

Kernel panic - not syncing:  Attempted to kill the idle task.

All my hardware is new, and Gutsy has been up and running fine until this afternoon, when it was non-responsive.  The screen wouldn't switch on even though the machine was obviously running, so I reset it manually and then got this error.

I've googled a bunch, and found that it may be helpful to run memtest - which I'm doing and is reporting a whole lot of errors.  So I've taken out one of the sticks of ram, and the machine then boots just fine.

The motherboard I was using recommends dual channel RAM, but I was using 1 extra 1gig stick to make my total ram up to 3gig.  This was working fine for days, so is there any chance of getting it to have all 3 again, or is the odd one fried?

---

### Post by mister_pink on 2008-01-19
Sounds like it's fried to me. If it's new, and definitely the right sort for your machine, then send it back. I've had generic RAM fail on me before, usually happens just after the warrenty runs out of course...

---

### Post by Squizz on 2008-01-19
It's a stick that I bought ages ago by mistake.  It's DDR2 and my old machine didn't support it (but I didn't realise at the time) - shame really :(

I've had some odd things go on when rebooting now though.  Out of 3 reboots, the first hung just after login on the desktop, the second hung as Ubuntu was making its startup noise and crashed - and the third is stable, but a few programs won't start up (like my dock).

---

### Post by mister_pink on 2008-01-19
Is this all without the third stick in? Try running memtest again without it in to check your other ram too. I had some ram fail a while ago when I was still using XP, and it only appeared as random bluescreens when I was doing memory intensive things.

---

### Post by Squizz on 2008-01-19
memtest doesn't appear to be giving me any errors, but reboot number 4 gave me:

Kernel panic - not syncing: Attempted to kill init

edi: and yes, I've put the older stick away now - will dispose of it next time I take a computer to be recycled.

---

### Post by mister_pink on 2008-01-19
I would wait for some other opinions before you chuck it out, I could've been jumping to conclusions, if taking it out hasn't fixed the problem entirely then it suggests that either it wasn't (completely) to blame, or its done some damage somewhere along the way. 

Next time you get a kernel panic, make note of what it said immediately before the actual error message

---

### Post by Squizz on 2008-01-19
I'm now getting random system crashes.

My login screen is always on the wrong resolution when I reboot, and my system now freezes completely, or goes to a black screen for no discernible reason.  If either of those things happen it doesn't recognise the mouse or keyboard and I have to just press the reset switch.

I don't even know where to start with troubleshooting here...

---

### Post by st33med on 2008-01-19
Sounds like a trashed motherboard. Maybe you need to replace it or get it shipped to get it fixed.

---

### Post by Squizz on 2008-01-19
> **st33med said:**
> Sounds like a trashed motherboard. Maybe you need to replace it or get it shipped to get it fixed.

How would I go about testing/proving that?  I ordered it from the internet, so it would need to be sent back there for testing and I'd be without a computer, so I don't really want to do that unless I'm sure.

---


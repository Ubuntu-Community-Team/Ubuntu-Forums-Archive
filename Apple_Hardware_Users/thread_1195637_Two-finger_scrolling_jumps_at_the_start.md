---
title: "Two-finger scrolling jumps at the start"
date: 2009-06-24
forum: Apple Hardware Users
---

### Post by elamericano on 2009-06-24
I've read lots of posts about touchpad configuration, but I still can't get my MacBook 4,1 configured right. The main problem is that putting two fingers on the pad usually makes it jumps a few lines up. So, two-finger scrolling down sometimes doesn't make any progress. Worse, right clicking with two fingers + click is like trying to hit a moving target.

Where can I get the full and current list of touchpad options for my device? I've seen older posts whose options do not appear to apply any more.

I think the driver should be smart enough not to scroll when a second finger is placed on the pad. This was a problem for pads that could not detect two fingers. Putting one finger low and and adding the second one high would make it read your one-finger position as being in the middle. But for a multi-touch pad, it should know your first finger hasn't moved. I'm not scrolling yet! I just put a second finger down.

Consciously pressing my two fingers together mitigates the problem, but it'll still scroll a line half the time. It's unusable in its current configuration.

---

### Post by Richardcavell on 2009-06-24
Elamericano,

It's a known problem for Ubuntu (and all other Linux distros, as far as I know).  It doesn't exist for Windows or OS X.

Lots of us have exhaustively played with all the settings that can be set, and there's no way to fix it.  If you want to try, please go ahead, and tell us if you find a solution, but I don't think you will.

The solution will be at source-code level, in a kernel driver.  I've filed a bug report about it.

Richard

---

### Post by jimv on 2009-06-24
That's so odd...I never noticed a problem with it.  I also didn't know you could scroll with two fingers.  I've been using the two-finger-tap as a middle click (for opening tabs and what not), but the two finger scrolling works for me too.  I actually am having trouble getting it to scroll on accident on my laptop....hmmm.  Seems like it only happens if I roll one of my fingers a little while tapping.

---

### Post by Richardcavell on 2009-06-24
Jimv,

It appears that the problem is with the appletouch touchpads, which is MacBook 1st through 4th generation, and MacBook Pro 1st through 3rd generation.  If your Mac laptop is earlier or later, you won't have this problem.  Since you say you are able to multi-touch, I'm guessing you have a recent one.

Richard

---

### Post by jimv on 2009-06-24
Oh, it's not even a Mac.  It's an older Gateway.

---

### Post by Richardcavell on 2009-06-24
Well, Jim, this is an Apple forum.  There is a known issue with the type of touchpad found in Mac laptops from late 2006 through about 2008.  I guess Gateways don't have that problem.  Consider yourself lucky.

Richard

---

### Post by jimv on 2009-06-24
My mistake, I've been accessing the forums from Google Reader, so I didn't notice which subforum it was.

---

### Post by hanzomon4 on 2009-06-25
[It's been reported and is being worked on]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/381884")

---

### Post by fbugnon on 2009-06-26
> **elamericano said:**
> (...) The main problem is that putting two fingers on the pad usually makes it jumps a few lines up. So, two-finger scrolling down sometimes doesn't make any progress.(...)

It's what I call a tap-scrolling...

While a solution is being working on, you can try to get used to either put both fingers down at the same vertical level of the  touchpad or (if you just want to avoid the jump up but doesn't mind a little jump down) put the upper finger first ;).

---

### Post by Tknab on 2011-04-20
Sorry to dig up an old thread, but I decided to give Ubuntu another shot on my almost 4 year old Macbook Pro (3,1). Nearly everything is working great but I'm still having the issue described in this thread and in the bug-report linked to previously in this thread. If I put my middle finger down first and then my pointer finger down below it everything is fine, if I put my pointer down first and then my middle finger down above it (what I normally do!) then the page immediately jumps up a few lines. Discussion in the bug report thread seems to have stalled and this thread has been dormant for a long time, but I was just hoping maybe somebody had found a fix for this at some point or could offer some suggestions.

Thanks

---

### Post by Never even on 2011-04-20
Thanks for the link, added my bit about Lucid.
(My first bug report thing!)

---


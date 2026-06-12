---
title: "Mac Mini (Intel) suspend"
date: 2008-02-01
forum: Apple Intel Users
---

### Post by ChrisMP1 on 2008-02-01
I have just installed Ubuntu alongside Tiger using rEFIt -- if all works out well I'll get rid of Tiger. However, I have one problem. Suspend.

I can suspend (even used acpitool to allow the keyboard to wake it), but the problem is that it never wakes. The pulsating power light freezes and it just sits and does nothing. Considering I never shut off my computer, I'd really like to get suspend working! Any help?

---

### Post by entangled on 2008-02-02
Sorry to hear you have the same problem as me. 
I've got an Intel Mac Mini Core Solo (First gen) and I want to get it to suspend and resume in Ubuntu.
In Feisty it would not even suspend. A message implied not implemented.
In Gutsy it suspends but never wakes. If I press the power button I get the system led on and the mouse led too, but no disk noise and no video.
I've had several pieces of advice on this forum but so far nothing works.
I've tried SUSE 10.3 as well. That also suspends but doesn't resume.

We might have to wait for a later kernel; I'm thinking of posting a bug in launchpad to try to relate the problem to mac mini but I think this is a kernel problem.

---

### Post by entangled on 2008-02-03
Success!
I installed kernel 2.6.24-5 from Hardy Heron.
It suspends on request.
To wake it up you have to touch the power button. After 2s the disk starts up and the led shows. After 10s the screen lit and I got a password prompt. First time with ubuntu.
I'll be keeping the new kernel.

---

### Post by cyberdork33 on 2008-02-03
> **entangled said:**
> Success!
I installed kernel 2.6.24-5 from Hardy Heron.
It suspends on request.
To wake it up you have to touch the power button. After 2s the disk starts up and the led shows. After 10s the screen lit and I got a password prompt. First time with ubuntu.
I'll be keeping the new kernel.

Excellent! You ought to keep up with the current testing kernel, and if it breaks be sure to file a bug report that already working behavior as broken. This will better ensure the capability makes it into the final builds.

---

### Post by wahr on 2008-02-03
please post or link in a how-to on that.

I'd love to do it.. without mucking it up : P

---

### Post by ChrisMP1 on 2008-02-03
I tried the newer kernel. It went a bit farther, taking me to a black screen with a mouse pointer (the mouse pointer could move). Still not good enough -- I'm going to compile the kernel myself and see if I can't find some hidden option somewhere in the kernel config that makes it work.

---

### Post by cyberdork33 on 2008-02-04
> **ChrisMP1 said:**
> I tried the newer kernel. It went a bit farther, taking me to a black screen with a mouse pointer (the mouse pointer could move). Still not good enough -- I'm going to compile the kernel myself and see if I can't find some hidden option somewhere in the kernel config that makes it work.That sounds like the video driver is not unloading or something.

---

### Post by romainrossi on 2008-02-25
Hi Guys,
Any Guide or step-by-step on how to solve this problem would be *greatly* appreciated.
Thanks in advance!

---

### Post by cyberdork33 on 2008-02-25
Apparently, upgrading to the Hardy kernel makes this work. Try that:
[http://ubuntuforums.org/showthread.php?t=646755](http://ubuntuforums.org/showthread.php?t=646755)

---


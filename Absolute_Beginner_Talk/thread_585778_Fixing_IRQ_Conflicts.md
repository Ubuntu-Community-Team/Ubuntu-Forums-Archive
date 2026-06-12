---
title: "Fixing IRQ Conflicts"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by plinydogg on 2007-10-21
Hello everyone,

I finally have Gutsy installed, compriz running, etc. but I'm now having the perennial wireless problems. I've got a Broadcom4318 wifi card and I've enabled the restricted drivers module but it still isn't working.

In Feisty, the only way I ever got wifi working was after I dealt with an IRQ conflict by doing this:

(1) Finding the most recent kernel line in menu.lst, which looked like this:

       * kernel          /boot/vmlinuz-2.6.17-11-generic root=/dev/hda1 ro quiet splash*

(2) Adding the following to the end of that line (after "splash"):

       *irqpoll noapic *

The only problem is that this doesn't seem to be working in Gutsy. Does anyone know how to fix the problem (I'm not even sure how to determine if there is an IRQ conflict, much less how to fix one in Gutsy!).

Thanks in advance!

Plinydogg

---

### Post by plinydogg on 2007-10-21
One thing I forgot to add: adding the "irqpoll noapic" like I did in Feisty caused Ubuntu not to boot and I had to reinstall!!!

---

### Post by plinydogg on 2007-10-21
Nevermind. Apparently, I don't even need to worry about it.

My wireless wasn't working but once I installed Wicd everything is working great now!

---


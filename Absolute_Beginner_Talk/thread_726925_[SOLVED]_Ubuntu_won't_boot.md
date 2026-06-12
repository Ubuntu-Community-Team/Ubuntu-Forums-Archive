---
title: "[SOLVED] Ubuntu won't boot"
date: 2008-03-17
forum: Absolute Beginner Talk
---

### Post by SpongeBob SquarePants on 2008-03-17
Hi all,

Have just built a new machine and am having trouble booting Ubuntu 7.10 (or in fact any Ubuntu version).

What happens is this. I boot up the Live CD and choose the safe graphics option (as I have a nVidia 7600 card). Anyway, it always kernel panics. So I reboot and use "noapic", which usually gets me as far as the splash, which loads, and the little bar thingy darts around as it should. But there is no disk activity, or any activity whatsoever. It just sits at the splash window for a few minutes before going to a black screen, with a flashing cursor.

Amy ideas on what I might try?

Bob

P.S. Have tried all the other boot options, all to no avail.

---

### Post by Ub1476 on 2008-03-17
Is the CD working at all? You can check the Cd for errors from the menu.

---

### Post by SpongeBob SquarePants on 2008-03-17
> **Ub1476 said:**
> Is the CD working at all? You can check the Cd for errors from the menu.

In a word, no!! The version of Ubuntu I was using didn't have the check CD option as it was a "Linux Format" cover disk. But I do have a disk with Kubuntu 6.10 on it and I tried to check the CD with that disk.....same...first a kernel panic and the suggestion to try booting with "noapic". So I reboot with "noapic" and get as far as the splash....but no disk activity.

So I'm presuming Ubuntu for some reason isn't getting on with my CD drive. Anything I can do about that? It's just a bog standard DVD burner type drive.

---

### Post by njparton on 2008-03-17
as well as adding noapic also remove splash from the same line (or add "nosplash" if it isn't there).

---

### Post by penguinpi.com on 2008-03-17
Try this, when you get the install screen press F6 and type irqpoll at the end. I have had similar problems in the past and sometimes it's an interrupt issue with the hard drive.

---

### Post by SpongeBob SquarePants on 2008-03-17
> **penguinpi.com said:**
> Try this, when you get the install screen press F6 and type irqpoll at the end. I have had similar problems in the past and sometimes it's an interrupt issue with the hard drive.

Dear God, the turn over of posts on this board is alarming. I posted a problem, nipped out for some shopping, came back and my post was on page eight....lol.

Anyway, just a quick thank you for the "irqpoll" tip. That seemed to get me past the glitch I was experiencing. What is interesting is I've had a similar problems with this on a few distro's....so I'm hoping this fix will work for those too.

Much obliged for everyone's help.

---


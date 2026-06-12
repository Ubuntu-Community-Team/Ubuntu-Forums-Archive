---
title: "A few very-beginner problems (OpenCD &amp; wireless 'net)"
date: 2006-07-29
forum: Absolute Beginner Talk
---

### Post by berniefranks on 2006-07-29
Okay, I am new to the Linux World (as I'm sure you'll be able to tell) and Ubuntu was suggested as a good starting point by some of the Linux folks to whom I talked.

I have two computers: a Dell Dimension 4300 and some eMachines one. The Dell is the one I am ultimately looking to install it on. However, it refuses to boot from the OpenCD. I tried it on my brother's Dell (his is the newest computer in the house), and it still didn't work. Both of them just boot up normally even after I went and changed it to boot from the disc drive. But when I tried it on my eMachines, it worked fine. After a whole lot of bad noise, I finally figured out how to get it out of 640x480 (I had been taking really difficult lengths to fix it, but it ended up just needing one simple command line :D). And what I've seen so far in this thing, I've enjoyed. So my question is: why does the disc not boot on my Dell and is there anything I can do to fix it?

Now after that, there's also the problem of internet. We have SBC DSL with the main router (a Speedstream 5360) downstairs hooked up to a Mac, and then my computer has a SpeedStream 1022 Wireless USB Adapter. From what I could gather, I take it that USB wireless adapters are not so hot with Linux? Is there any way to make this adapter work with Linux? What are my options?

And that's all I've got for now - thanks in advance. :)

---

### Post by Apple 101 on 2006-07-29
Was the USB adapter detected? Open a terminal and type: *dmesg*.  Look for the adapter.

---

### Post by berniefranks on 2006-07-29
I tried dmesg and I couldn't find it.

---

### Post by berniefranks on 2006-07-30
Any others ideas? Or ideas on how to get the boot disc to work on my Dell?

---

### Post by Apple 101 on 2006-07-31
Have you tried the Live CD or the alternate CD?  Have you been able to boot from any CDs (not just Ubuntu) upon computer startup?

---


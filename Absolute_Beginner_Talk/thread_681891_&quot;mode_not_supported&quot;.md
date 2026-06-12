---
title: "&quot;mode not supported&quot;"
date: 2008-01-29
forum: Absolute Beginner Talk
---

### Post by dsds on 2008-01-29
Hi

I've just installed ubuntu studio but when the "loading screen" (is this known as the splash screen?)starts I receive a message from my monitor MODE NOT SUPPORTED H: 74.6 KHZ V:59.7HZ

I'm a newbie, but looking through other posts I'm guessing it's to do with my graphics card. So I started in recovery mode, made my way to menu.lst and found the bit which said "ro quiet splash".

Could you tell me if this is what I need to change to avoid the graphics whilst loading - and if so what do I change it to?

Many thanks

Dave

---

### Post by spiderbatdad on 2008-01-29
you could try nosplash  all one word. But this seems like a bios issue. Do you have display settings in your bios?
For example, in my bios, I navigate to config>>display, and from there can select a primary device as pci, and then there are graphics modes like analog+vga.

If that doesn't work you might try deleting everything in that kernel line back to and including "ro" and replace with noapic nolapic

---

### Post by dsds on 2008-01-29
Hi

thank you for your reply .... unfortunately that didn't turn out to be the cause of the problem which is still there.

Re: my bios - my PC dual boots to Windows, and I've tried a couple of other linux distros in the past few days which didn't have this problem, so I don't think the problem can be with the bios?

Best wishes

Dave

---

### Post by spiderbatdad on 2008-01-29
maybe you could post your video card. there are several other xserver-xorg-ati video drivers in synaptic.
seems like your display settings are not supported though. idk if grub can do anything about that without the right drivers, obviously.
At grub prompt you can view commands and examples with F6 then F1, i believe.
It seems if other linux distros supported your bios display settings, then ubuntu would as well.
You might try adding vga=792 to the end of your kernel line...though the driver issue is probably the thing to explore.

---


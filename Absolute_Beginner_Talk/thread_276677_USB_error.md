---
title: "USB error"
date: 2006-10-13
forum: Absolute Beginner Talk
---

### Post by SpaceBanana on 2006-10-13
Hey there, Ubuntu beginner here, maybe you can help...

When booting Ubuntu from CD I get the error message
[17179601.552000] usb 3-2.3: device descriptor read/all, error -110

I figured it was probably my USB bluetooth tranceiver (for keyboard and mouse), but when I removed that and tried booting with a USB mouse and PS/2 keyboard, Ubuntu hangs while "mounting root file system" without an error message.

Any ideas?

Cheers :)

---

### Post by petri on 2006-10-13
There is several ways to fix that, try first to boot with **acpi=off** (just write it) after you press the **F6** button at LiveCD start. If it doesn't work you could do a Search and try the alternatives you find.

And post you pc brand and model, videocard etc. if you don't find anything.

---

### Post by SpaceBanana on 2006-10-13
Thanks for the quick reply!

I tried your suggestion but it then gave me an message to the effect that the PnPBIOS had caused a fatal error. I also tried both  acpi=off and pnpbios=off, but this just took me back to the original problem. Hmm...

System specs:
Intel Core 2 Duo E6300
Asus P5B
Nvidia 7600GT
LG DVDRW
1GB DDR2 RAM
250GB hard drive separated into 3 partitions, 2x 20GB (one with XP installed, the other with Vista build 5728 ) and 1x 210GB for data.

Are there any known compatability issues with any of this hardware?

---

### Post by dillbertdabomb on 2006-10-13
your graphics card, nvidea isn't supported yet

and maybe your dvd drive, mine can be stupid like that at times...

---

### Post by jcrnan on 2006-10-13
have you tried booting from another cd (in case the cd is corrupt)?

---

### Post by redbull_monsta on 2006-10-13
> your graphics card, nvidea isn't supported yet

This wont cause a problem with the live CD as it uses standard vesa driver surely.....

---

### Post by SpaceBanana on 2006-10-13
> have you tried booting from another cd (in case the cd is corrupt)?
I think the CD's OK... a friend just tried booting from it and it worked fine in his laptop

---

### Post by SpaceBanana on 2006-10-14
Anyone have any more ideas? Still can't seem to get it to work...

Cheers

---

### Post by petri on 2006-10-14
There have been problems with SATA harddrives, I don't have one so I haven't read those so closely.

Other optins to boot with: IDE=NODMA and PCI=NOACPI and there must be others too when you push the F6 button.

As I said before have you done a Search up at title bar? There is many threads about this problem and there sure are many answers too, one was playing with the BIOS with some . Sorry to send you away alone like that but there are simply too many different answers.

But ask here if you don't understand something or in that special thread and please return to this thread after you solved the problem so the next one coming after you may find a solution more easily.

---


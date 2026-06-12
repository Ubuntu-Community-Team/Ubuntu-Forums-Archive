---
title: "Auto update &quot;upgraded&quot; and now stalls when it loads :("
date: 2008-04-11
forum: Absolute Beginner Talk
---

### Post by h-town on 2008-04-11
The Ubuntu loading bar that starts up when I start up my pc freezes exactly mid-way through the third bar. 

I don't have to reinstall ubuntu again do I :mad:

---

### Post by spiderbatdad on 2008-04-11
probably not. Does the system eventually start if you wait 5-6 minutes?
At start up press 'e' at the grub menu to edit the kernel you are going to boot. Use the arrow key to move to the line that starts with 'kernel' press 'e' again...go to the end of that line, and delete quiet splash. Press 'b' to boot...watch the process to see where it hangs.

---

### Post by h-town on 2008-04-12
alright, I did what you said and here is the section it freezes on, I waited 10-15 minutes

* Setting the system clock
* Loading Kernel modules...
* Loading manual drivers...

and then nothing.

---

### Post by spiderbatdad on 2008-04-12
ok try this please:

edit the kernel line again in grub. I'm sorry I can't be sure of the parameters the first time through, but no harm will be done. If this is successful, you will need to make the entry permanent in /boot/grub/menu.lst

Press 'e' to edit the kernel you wish to boot (the highlighted one) arrow key to the line beginning with 'kernel' Press 'e' again. Delete 'ro quiet splash' and replace with 'lapic pci=routeirq' (no single quotes) Hit enter and press 'b' to boot. Hope it works.

lapic is all letters not 1apic.

---

### Post by h-town on 2008-04-12
that didn't work, unfortunately. it still freezes on the same line.

---

### Post by Kevkill on 2008-04-12
Exactly the same problem here. I did a full reinstall and update and it still hangs in the same spot. I have reinstalled again but am afraid to update until I find out what the problem is.

---

### Post by hyper_ch on 2008-04-12
does the recovery mode work?

---

### Post by spiderbatdad on 2008-04-12
> **h-town said:**
> that didn't work, unfortunately. it still freezes on the same line.

Sorry you are having this issue. I know it's frustrating. Do you still have an earlier kernel version in the grub menu you can use, ie. 2.6.22-14?
There are a few other parameter options you can try, and possibly solve the problem.
option 1: noapic nolapic vga=792
option 2: noapic
option 3: nolapic

If you press F6 at the grub menu and then F1, I think...and F6 again, you can get a description of some of these parameters, and possibly better insight than I can provide.

---

### Post by h-town on 2008-04-13
Well I was able to load into one of the slightly older versions on my boot menu. This will appease me for a short while. I have like three options for ubuntu with each having a recovery option as well. I'll try what you said and update this thread with the results in a while.

---

### Post by diablo75 on 2008-04-13
There are some updates yet to be released for the latest development kernels.  I had the same issue with my Beta release of Hardy using Kernel 16.  I had to revert to 15 or earlier to boot.  The problem went away on one PC after further kernel module updates downloaded, but I'm still waiting for the kinks to work itself out on the other PC.  No big deal for now.  I can just tell it to boot from a previous kernel version in the mean time...

---


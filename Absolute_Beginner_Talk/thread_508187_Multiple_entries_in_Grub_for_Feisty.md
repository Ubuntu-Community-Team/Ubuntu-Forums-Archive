---
title: "Multiple entries in Grub for Feisty"
date: 2007-07-23
forum: Absolute Beginner Talk
---

### Post by scorpio54 on 2007-07-23
I installed Feisty yesterday on my system to give it a test drive. New to Linux and pissed off at Micro$oft. But that's another story. I now have 3 operating systems ( XP Pro, Vista, And Feisty) all of which work and boot up fine. But in my Grub boot menu I have 2 Feisty Fawns boots and recovery options. The install froze on me the first 2 times I attempted it and third time was a charm as they say. First try got almost finished then froze up. Is this why its lists  twice. When I open the Grub menu this is what I have:


title		Ubuntu, kernel 2.6.20-16-generic
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=da329a8e-a911-42fb-8616-81a9289ef28d ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=da329a8e-a911-42fb-8616-81a9289ef28d ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=da329a8e-a911-42fb-8616-81a9289ef28d ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=da329a8e-a911-42fb-8616-81a9289ef28d ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd1,2)
kernel		/boot/memtest86+.bin
quiet

Can I just edit the second listing (2.6.20-15)out of menu and get rid of it? It loads fine with the (2.6.20-16) at start up menu. Thanks for any help that can be offered.

---

### Post by Nekiruhs on 2007-07-23
Yes you can. Its only there as a backup, if you break your current one, you have a fall back.

---

### Post by scorpio54 on 2007-07-23
So what your saying is they are both supposed to be there in case one gets corrupted. Never would have guessed that. I will leave it be if that is the case. Thanks for your quick response. This is all so new to me. This forum is great!!:KS Looking forward to weaning myself off Windows.

---

### Post by Nekiruhs on 2007-07-23
Yeah. you got it exactly. BTW, if you ever do need to remove an entry just comment it out. GRUB ignores any lines starting with # as human readable comments. Dont delete the lines just put a # at the beginning of the line. That way if you need to get it back, just uncomment it by removing the #. (This works for almost all config files oo).

---

### Post by scorpio54 on 2007-07-23
Great advise!:KS

---


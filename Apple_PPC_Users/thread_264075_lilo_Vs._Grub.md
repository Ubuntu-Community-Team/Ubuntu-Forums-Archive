---
title: "lilo Vs. Grub"
date: 2006-09-24
forum: Apple PPC Users
---

### Post by ZERO_SHIFT on 2006-09-24
I am planning on buying a Macbook and was wondering what exactly is lilo, and how different is it from Grub.

Another concern I have is whether upadating will cause any problems on running/booting ubuntu on the Macbook, if so how can I avoid it.

Thanks

---

### Post by kidders on 2006-09-24
Hi there,

Lilo is perhaps a more straightforward bootloader than Grub ... I used it for years, mostly because Grub's insistence on numbering hard drives it's own way annoyed me. Grub is far more sophisticated though ... I'm not sure if I can think of a **real** reason to use lilo! (At least one that still exists.)

About your update-related concerns, I presume you're referring to updating OSX. In my experience, certain OSX updates can involve rewriting system areas of disks, which might break your bootloader. Often, the only way to recover is with a Linux boot disk.

---

### Post by ZERO_SHIFT on 2006-09-24
Hi

Thanks for the reply, however I was refering to the ubuntu update manager, will it affect ubuntu booting ??

Another question is which would be more stable Lilo or Grub??

---

### Post by kidders on 2006-09-24
Your choice of bootloader has no effect on anything really ... except your bootloader, that is. You don't have to do anything freaky to Ubuntu to get it to cooperate with Lilo, or any other bootloader :-)

In terms of stability, bootloaders don't tend to have any problems ... they're not exactly rocket science, so their developers usually get things right. Take a look at the feature lists of a few of your available choices, and try them :-)

In a single sentence, I suppose you could say that Lilo is easier to set up, but Grub is more full-featured. I hope that helps.

---

### Post by ZERO_SHIFT on 2006-09-25
Will updating through ubuntu update manager effect the booting of the system??

---

### Post by kidders on 2006-09-25
I suppose it may do, but that won't necessarily have anything to do with your choice of bootloader. Occasionally, people seem to run into difficulties after performing sweeping updates.

Specifically, kernel updates can be tricky ... regardless of the bootloader your choose, you should always check that any automated reconfiguration that took place is sensible.

I hope that answers your question.

---


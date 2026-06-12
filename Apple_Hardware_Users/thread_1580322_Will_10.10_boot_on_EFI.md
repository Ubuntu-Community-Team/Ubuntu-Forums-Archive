---
title: "Will 10.10 boot on EFI  ?"
date: 2010-09-23
forum: Apple Hardware Users
---

### Post by andreacfm on 2010-09-23
Looks like 10.10 will have grub2 and so the ability to boot on efi system. I have a macbook pro 6.2.
Will maverick install on this machine as normal dual boot with no need of refit support?

Thanks

Andrea

---

### Post by mgriepentrog on 2010-09-24
Unfortunately, it looks like the answer is no. I also have a MacBook Pro 6,2, and while I'm able to see the "EFI Boot" option when holding alt, it does not get past the grub boot loader. I haven't really been able to debug why it doesn't work as the screen goes blank when I try and load the live CD.

---

### Post by wbs75 on 2010-09-24
yes, it work for me on triple boot using sSATA external drive with bootable card.  I used refit for bootloader, install ubuntu last

---

### Post by mgriepentrog on 2010-09-24
Do you also have a MacBook Pro 6,2? It really varies by hardware. This appears to also be an issue for Fedora: [https://bugzilla.redhat.com/show_bug.cgi?id=528232](https://bugzilla.redhat.com/show_bug.cgi?id=528232). I'm downloading the nightly livecd now to see if I'm able to boot via EFI. If it is the same issue, the [fix]("http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commitdiff;h=a5757c2a474a15f87e5baa9a4caacc31cde2bae6") may make it in to the final version of 10.10, otherwise 11.04 for sure.

---

### Post by wbs75 on 2010-09-24
no, Mac Pro G5 INTELL early 2009 model

---

### Post by cwestpha on 2010-09-24
No, this is still a work in progress from GRUB 2's upstream. If it works at all expect the possibility of it breaking in future updates or with some issues.
Legacy (BIOS emulation) is still the best route for booting due to the differences between the normal EFI server and workstation platform (what the GRUB 2 EFI project is focused on), and Apple's striped and modified EFI implementation.

---


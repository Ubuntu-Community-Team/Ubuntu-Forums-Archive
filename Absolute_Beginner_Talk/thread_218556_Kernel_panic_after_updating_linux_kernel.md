---
title: "Kernel panic after updating linux kernel"
date: 2006-07-18
forum: Absolute Beginner Talk
---

### Post by guopai on 2006-07-18
Hi, I've using Ubuntu for less than a month. Just a few minutes ago I update the kernel through automatic update from 2.6.15.26-44 to 2.6.15.26-45. My PC is Athlon XP 2000+, and it use 386 version of kernel. They update process went just fine. As I inspect the terminal during the update, it automatically edited menu.lst and post no error whatsoever. When I reboot, the GRUB menu show only the latest kernel (it should show previous kernel doesn't it?) and I got error message:

[INDENT]CRC error
Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block (0,0)[/INDENT]

Recovery mode won't do either, it just add the line:

[INDENT]VFS: Cannot open root device "hda2" on unknown-block (0,0)
Please append a correct "root=" boot option.[/INDENT]

I'm pretty sure hda2 is my linux partition. I also have extra ext3 partition on hda4 (just take the space from Windows partition, which was a first partition in HDD).

Anyone please advise how to solve this. Thanks!

---

### Post by Afishionado on 2006-07-18
Something went wrong. :-k 

At the Grub boot menu, select the Ubuntu entry and press the e key, to interactively edit the boot options. Then:

[LIST=1]
[*]Write down exactly what the text you get is and post it here.
[*](Just guessing here...) If it's not already there, try adding this to the end of the options, and see if it boots: root=/dev/hda2
[/LIST]

---

### Post by guopai on 2006-07-18
> **Afishionado said:**
> Something went wrong. :-k 

At the Grub boot menu, select the Ubuntu entry and press the e key, to interactively edit the boot options. Then:

[LIST=1]
[*]Write down exactly what the text you get is and post it here.
[*](Just guessing here...) If it's not already there, try adding this to the end of the options, and see if it boots: root=/dev/hda2
[/LIST]

OK, here's what it said:

[INDENT]root (hd0,1)
Kernel /boot/vmlinuz-2.6.15-26-386 root=/dev/hda2 ro quiet splash
initrd /boot/initrd.img-2.6.15-26-386
save default
boot[/INDENT]

To my knowledge, I don't think there's any thing wrong with the boot commands...

---

### Post by guopai on 2006-07-18
Just re-install Ubuntu and updated the same kernel. Things went fine this time. If anyone have a clue how to prevent/sove this I'd appreciate if you share. Thanks.

---


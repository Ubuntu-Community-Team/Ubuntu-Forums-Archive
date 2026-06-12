---
title: "Question about Boot-up and such..."
date: 2005-08-12
forum: Absolute Beginner Talk
---

### Post by Muhammad on 2005-08-12
What's the diffrence between GRUB and BUM?

---

### Post by heimo on 2005-08-12
BUM is program to select which services and programs start at the boot. Grub is a program that allows to select which operating system or for example, which kernel version to boot - it's a "boot menu". Does this answer your question?

BUM
>  Boot-Up Manager is a graphical tool to allow easy configuration of init services in user and system runlevels, as far as changing Start/Stop services priority.
 [http://packages.ubuntu.com/breezy/admin/bum]("http://packages.ubuntu.com/breezy/admin/bum")

GRUB
 > 
GRUB is a GPLed bootloader intended to unify bootloading across x86 operating systems. In addition to loading the Linux kernel, it implements the Multiboot standard, which allows for flexible loading of multiple boot images (needed for modular kernels such as the GNU Hurd). [http://packages.ubuntu.com/breezy/admin/grub]("http://packages.ubuntu.com/breezy/admin/grub")

---

### Post by Muhammad on 2005-08-12
[QUOTE=heimo]BUM is program to select which services and programs start at the boot. Grub is a program that allows to select which operating system or for example, which kernel version to boot - it's a "boot menu". Does this answer your question?

BUM
 [http://packages.ubuntu.com/breezy/admin/bum]("http://packages.ubuntu.com/breezy/admin/bum")

GRUB
  [http://packages.ubuntu.com/breezy/admin/grub]("http://packages.ubuntu.com/breezy/admin/grub")[/QUOTE]
 OK thanks, one more question though,

GRUB loads too slow, why?

---

### Post by heimo on 2005-08-12
[QUOTE=Muhammad]OK thanks, one more question though,

GRUB loads too slow, why?[/QUOTE]

Could you describe what's happening? At what point of starting your computer, what's on the screen when it's slow? What I'm trying to ask here, is it a total pause at some point and if so, what's the last thing on the screen before that? You're probably experiencing some delays during boot, but probably not in grub itself.

---

### Post by Muhammad on 2005-08-12
[QUOTE=heimo]Could you describe what's happening? At what point of starting your computer, what's on the screen when it's slow? What I'm trying to ask here, is it a total pause at some point and if so, what's the last thing on the screen before that? You're probably experiencing some delays during boot, but probably not in grub itself.[/QUOTE]
 Before Ubuntu starts, I receive the message "GRUB stage 1.5 Loading..." or something similar, and then I'll have to wait for a minute or two before the splash screen appears and the rest of sequence. Is that normal?

---

### Post by heimo on 2005-08-12
[QUOTE=Muhammad]Before Ubuntu starts, I receive the message "GRUB stage 1.5 Loading..." or something similar, and then I'll have to wait for a minute or two before the splash screen appears and the rest of sequence. Is that normal?[/QUOTE]

Oh! That's not normal at all. I would probably try reinstalling grub or installing lilo (another boot loader). You can probably find instructions how to reinstall grub on these forums. Installing lilo may be as simple as *sudo apt-get install lilo *but I'm not sure. If possible, burn yourself Ubuntu Live CD or Knoppix Live CD at this point (unless you already have one), so you have a rescue CD, something to work with if your computer won't boot anymore.

Something about reinstalling grub (check at least posts one and two):
[http://www.ubuntuforums.org/showthread.php?t=24113](http://www.ubuntuforums.org/showthread.php?t=24113)

---

### Post by Muhammad on 2005-08-12
[QUOTE=heimo]Oh! That's not normal at all. I would probably try reinstalling grub or installing lilo (another boot loader). You can probably find instructions how to reinstall grub on these forums. Installing lilo may be as simple as *sudo apt-get install lilo *but I'm not sure. If possible, burn yourself Ubuntu Live CD or Knoppix Live CD at this point (unless you already have one), so you have a rescue CD, something to work with if your computer won't boot anymore.[/QUOTE]
 Yep, I already have the Live CD, thanks for the advice. :)

---


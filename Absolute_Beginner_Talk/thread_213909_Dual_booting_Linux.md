---
title: "Dual booting Linux"
date: 2006-07-11
forum: Absolute Beginner Talk
---

### Post by lennyjames on 2006-07-11
Hello everyone,
I'm new to Ubuntu and Linux, and am really enjoying this new OS! Great job to everyone who has made this terrific OS!

Anyway, I really like Ubuntu and what it is capable of, but I would like to give other distros a spin for learning's sake. Is it possible to dual-boot to another Linux OS on the same or slave drive?

---

### Post by user1397 on 2006-07-11
> **lennyjames said:**
> Hello everyone,
I'm new to Ubuntu and Linux, and am really enjoying this new OS! Great job to everyone who has made this terrific OS!

Anyway, I really like Ubuntu and what it is capable of, but I would like to give other distros a spin for learning's sake. Is it possible to dual-boot to another Linux OS on the same or slave drive?short answer: YES!

long answer: yes, but it can be a pain, because of the boot loader.  the new linux distribution will want to install their boot loader (most likely grub), which will overwrite your ubuntu grub, so then what you would want to do is copy all of your entries of your /boot/grub/menu.lst file to put it in your new grub.  I can help you out with that if you want.

---

### Post by dasunst3r on 2006-07-11
YES!  It is possible to multi-boot Linux distributions.  Just be careful when you partition.

---

### Post by lennyjames on 2006-07-12
> **erik1397 said:**
> short answer: YES!

long answer: yes, but it can be a pain, because of the boot loader.  the new linux distribution will want to install their boot loader (most likely grub), which will overwrite your ubuntu grub, so then what you would want to do is copy all of your entries of your /boot/grub/menu.lst file to put it in your new grub.  I can help you out with that if you want.

Thanks! I would like to give it a try. I currently run Ubuntu on an older machine (866MHz, 128 RAM, GEforce 4, DVD/CD-RWs) with an old 20Gb Quantum Fireball. I do have a spare 80Gb Maxtor that I can reserve for, say, a SUSE 10.1 or Mandrake 10.1. Initially I was going to remove the Fireball and make the Maxtor the master drive to avoid the hassle of dual booting but if there is a solution, I would be very grateful for any assistance. I'm still a little shaky using the termainal and don't quite undestand the Linux terminology and commands, but am not afraid to jump on in! :D 

However, the real pain is that this system needs a new modem and will not have one for about a week or two.

---

### Post by user1397 on 2006-07-12
> **lennyjames said:**
> Thanks! I would like to give it a try. I currently run Ubuntu on an older machine (866MHz, 128 RAM, GEforce 4, DVD/CD-RWs) with an old 20Gb Quantum Fireball. I do have a spare 80Gb Maxtor that I can reserve for, say, a SUSE 10.1 or Mandrake 10.1. Initially I was going to remove the Fireball and make the Maxtor the master drive to avoid the hassle of dual booting but if there is a solution, I would be very grateful for any assistance. I'm still a little shaky using the termainal and don't quite undestand the Linux terminology and commands, but am not afraid to jump on in! :D 

However, the real pain is that this system needs a new modem and will not have one for about a week or two.well, just PM (private message) me if you need any help.

---


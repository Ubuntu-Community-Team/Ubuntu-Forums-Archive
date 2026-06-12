---
title: "[SOLVED] Strange dual-boot problem."
date: 2008-06-26
forum: Arch and derivatives
---

### Post by ch_123 on 2008-06-26
Hi folks,

I have got myself a nice new Thinkpad laptop. In order to preserve its special recovery partition, I have installed GRUB onto my Linux partition as opposed to the MBR, and set my Linux partition to be the active partition using GParted. Now, this all worked fine until I booted into Windows. It seems that when Windows boots up, it suddenly turns its partition into the active one, so that when I restart, the computer boots directly into Windows without giving me the GRUB menu. I feel I might have stumbled up against some inherent limitation in GRUB and/or Windows, but if anyone knows a way around it without installing GRUB to the MBR, I would be delighted to know.

Thanks :)

---

### Post by Barrucadu on 2008-06-26
Have you tried editing your BIOS to boot from the Linux partition? As far as I'm aware an operating system can't change the BIOS configuration, that is, without overwriting all of it.

---

### Post by ch_123 on 2008-06-26
I wasn't aware a BIOS could be made to boot from a particular partition. In fact, I think that's the whole reason that bootloaders exist in the first place. And O/Ss can change which is the active partition, GParted is able to do it, for example.

---

### Post by Barrucadu on 2008-06-26
I seem to remember reading about it somewhere - but I can't remember how or where, so it's probably useless.

---

### Post by mips on 2008-06-27
> **ch_123 said:**
> I wasn't aware a BIOS could be made to boot from a particular partition. In fact, I think that's the whole reason that bootloaders exist in the first place. And O/Ss can change which is the active partition, GParted is able to do it, for example.

I'm  not aware of that either. The only thing you can specify is the physical drive you want to boot off.

---

### Post by ch_123 on 2008-08-12
I decided to retry the installation, and whilst configuring GRUB I realized what the problem was; by default, GRUB's entry for Windows includes the command "makeactive" which, as the name suggests, makes the partition active once it is booted. Removing this line from menu.lst keeps the Linux partition as the active one. Problem solved. :)

---


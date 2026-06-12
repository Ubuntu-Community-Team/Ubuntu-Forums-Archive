---
title: "What will happen if.."
date: 2007-04-12
forum: Absolute Beginner Talk
---

### Post by shazzed on 2007-04-12
Firstly will Fiesty ubuntu detect SATA drives to install on, without a stupid floppy driver like Win XP ?

if so...

What will happen if I install UBUNTU on a SATA then install Win XP onto a PATA (different drive)

Will I have to change my boot device each time to switch OS ? 
or will XP see the other os and add it to it's boot manager?

I want to keep the two Operating Systmes as apart as I can before I go completely feral and ditch XP all together.
Any help/advice would be great
cheers

---

### Post by bwhite82 on 2007-04-12
From experience, I would recommend installing windows first, then Ubuntu. Either method can be used, however, but grub simply does a better job of detecting other OSes and automagically making them active on the menu.lst.

---

### Post by darkrose on 2007-04-12
Shouldn't be any problem with Ubuntu on a SATA drive, no floppy required.

However, if you do what you say, install windows first, then when you install Ubuntu it will detect windows and add it to the boot menu (you could add Ubuntu to the windows boot manager, but from what i hear it's a lot of stuffing about).

---


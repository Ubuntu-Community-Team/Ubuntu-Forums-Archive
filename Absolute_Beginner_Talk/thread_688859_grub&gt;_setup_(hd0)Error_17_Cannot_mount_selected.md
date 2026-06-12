---
title: "grub&gt; setup (hd0)

Error 17: Cannot mount selected partition"
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by rmx on 2008-02-05
Hello.

I have a system with xp and ubuntu.

I erased my ubuntu partion and restored a saved one from a backup.

I found this error before boot menu: error 17.

I run live cd (7.04) and launched a terminal:

```
grub

grub> find /boot/grub/stage1

Error 15: File not found

grub> root (hd0,5)

grub> setup (hd0)

Error 17: Cannot mount selected partition

```

My ubuntu partition is on sd6, and /boot/grub/stage1 existes, does anyone have a clue

thanks 

RMX

---

### Post by Linux_Man on 2008-02-05
What type of hard drive is it? Is it configured on a RAID? Is it internal or external? Can you boot XP just fine? Because if so then it chances are its not a hardware issue.

---

### Post by rmx on 2008-02-05
it is an IDE internal HD.

booting from HD just makes error 17 before grub menu
I can-t see ubuntu grub menu, so I can-t acess xp also.

---


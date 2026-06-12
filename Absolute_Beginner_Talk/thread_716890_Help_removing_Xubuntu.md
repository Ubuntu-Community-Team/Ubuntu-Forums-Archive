---
title: "Help removing Xubuntu"
date: 2008-03-06
forum: Absolute Beginner Talk
---

### Post by medic8ted on 2008-03-06
I want to start trying new distros, but how to remove them without f-ing up GRUB?  I've installed Xubuntu, and now want rid of it.  I'm afraid if I just format that partition, GRUB will not be happy.  I want to keep GRUB happy.  Am I thinking right?
EDIT: Dell Optiplex 40g HD with 4 partitions, Gutsy 7.10 on #3, Xubuntu 7.10 on #1, storage on #2, swap on #4

---

### Post by taurus on 2008-03-06
Is Xubuntu the only OS on your machine?  What is the other distro(s) you plan to check out?  If you remove Xubuntu, then GRUB won't boot since it will look for the entries in /boot/grub/menu.lst.  And if you plan to install another distro, it will create it own GRUB or Lilo, depending on which distro you install.

---

### Post by medic8ted on 2008-03-06
I don't know which other distros to try, I just enjoy breaking things and fixing them.  Hence the switch to Ubuntu.  Windows free since 1/1/08.

---

### Post by taurus on 2008-03-06
If you install another Linux distro, it will install it own version of GRUB or Lilo on the MBR so I wouldn't worry too much about GRUB version of Xubuntu.

---

### Post by medic8ted on 2008-03-06
Just edit menu.list so it goes to Ubuntu 1st instead of Xubuntu?

---

### Post by Rytron on 2008-03-06
If you do cause unintended damage to the grub - try [Hirens boot cd]("http://www.zshare.net/download/385931ab6f96/").
Its got loads of tools for formatting partitions, wiping hdd, grub loaders, etc.

---


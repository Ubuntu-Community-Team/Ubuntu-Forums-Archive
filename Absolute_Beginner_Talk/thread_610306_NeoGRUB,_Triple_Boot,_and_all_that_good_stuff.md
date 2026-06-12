---
title: "NeoGRUB, Triple Boot, and all that good stuff?"
date: 2007-11-11
forum: Absolute Beginner Talk
---

### Post by shamushand on 2007-11-11
I need help - after being disappointed that XP can't be booted directly through GRUB along with Vista due to BCD, I'm still trying to get everything under one nice, tidy boot menu.

Let me explain my setup:

1st Hard Frive
[LIST]
[*]1st Partition: Windows Vista
[*]2nd Partition: Games
[/LIST]

2nd Hard Frive
[LIST]
[*]1st Partition: Windows XP
[*]2nd Partition: Ubuntu 7.04
[/LIST]

Order in which I installed OS'es:
[LIST]
[*]Windows Vista
[*]Windows XP
[*]Ubuntu 7.04
[/LIST]

My boot menus:

GRUB
[LIST]
[*]Ubuntu 7.04
[*]Windows XP/Vista
[/LIST]

Then once 'Windows XP/Vista' is selected:
[LIST]
[*]Windows Vista
[*]Windows XP
[/LIST]

The point is: I want GRUB gone, and I want EasyBCD with NeoGRUB to manage everything. How do I get started? All help appreciated! :)

---

### Post by louieb on 2007-11-11
What the difference between this thread and your other thread?
[http://ubuntuforums.org/showthread.php?t=609990](http://ubuntuforums.org/showthread.php?t=609990)

The answers to your questions can be foud at:   [Illustrated Dual Boot Site]("http://users.bigpond.net.au/hermanzone/")

---

### Post by Computer Guru on 2007-11-13
Copy your /boot/grub/menu.lst to the NeoGrub configuration file in c:\nst\menu.lst

---


---
title: "resetting default and wait time in GRUB"
date: 2006-12-26
forum: Absolute Beginner Talk
---

### Post by GreetingsEarthling on 2006-12-26
Hi,

I would like to have my computer default to booting to my existing Win2000 installation rather than to Ubuntu. I was going to follow the instructions posted [here]("http://www.computing.net/linux/wwwboard/forum/28944.html") (substituting menu.lst for grub.conf) but I was not able to save the file, it tells me I do not have sufficient "permissions". I suspect this is a simple problem . . . what do I do?

Thanks in advance for your help.

---

### Post by dbbolton on 2006-12-27
use sudo

```
 sudo gedit '/boot/grub/menu.lst'
```:D

---


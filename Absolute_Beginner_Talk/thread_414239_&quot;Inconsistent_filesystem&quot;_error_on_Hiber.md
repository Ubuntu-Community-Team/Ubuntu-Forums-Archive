---
title: "&quot;Inconsistent filesystem&quot; error on Hibernate resume in Feisty"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by tezem on 2007-04-19
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/grub/+bug/64928](https://bugs.launchpad.net/ubuntu/+source/grub/+bug/64928) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I realized that I get an error when I Hibernate my Feisty laptop.
Everything works fine but when I select the normal boot kernel for Ubuntu in grub I get: "Error 16: Inconsistent filesystem structure"
Selecting the recovery boot option boots up the machine correctly and the machine shows everything like before the hibernation.

I found that the problem is grub related as you can see here: [https://bugs.launchpad.net/ubuntu/+source/grub/+bug/64928](https://bugs.launchpad.net/ubuntu/+source/grub/+bug/64928)

So to simply solve this remove the savedefault entries away from the /boot/grub/menu.lst.

---


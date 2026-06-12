---
title: "GRUB Bootloader order?"
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by Jdratcliffe on 2007-05-15
is there any way of changing the order - i have a duel boot system but it defual to ubuntu great for speed boots but most of the time i boot pc and walk away needing windows. any ideas ....

---

### Post by indytim on 2007-05-15
This should help you along:

[http://users.bigpond.net.au/hermanzone/]("http://users.bigpond.net.au/hermanzone/")

IndyTim

---

### Post by wormser on 2007-05-15
Yes you can change the boot order.

```
sudo gedit /boot/grub/menu.lst
```

Look for the line:

> default		0

The 0 means it is going to boot the first one on the list.  Scroll to the bottom of the page to ## ## End Default Options ##.  Starting at the top counting from 0 to the one you want to boot.  Put that number in place of the 0 on the default line.  Save and reboot and see if it works.

---


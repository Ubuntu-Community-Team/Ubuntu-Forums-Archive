---
title: "How do i edit Grub's order"
date: 2007-12-26
forum: Absolute Beginner Talk
---

### Post by supernoob on 2007-12-26
I was wondering - could i change grub to load windows by default instead of Ubuntu (since I'm the only one who uses Ubuntu)

---

### Post by philinux on 2007-12-26
If you want to do it with a gui, then install and run startupmanager from synaptic.

---

### Post by taurus on 2007-12-26
Yes.  Just change the **default** from 0 to whatever the number of your windows in /boot/grub/menu.lst.

```
gksudo gedit /boot/grub/menu.lst
```
Remember, each line with **title** means one and you start counting from 0.

---

### Post by LinuxIsInnovation on 2007-12-26
sudo gedit /boot/grub/menu.lst

There are 4-5 lines for Windows at the bottom (Identify by "chainloader" and  "makeactive" keywords)
Simply copy them to the top of the other options.

BE CAREFUL BEFORE EDITTING THIS FILE.

---

### Post by overdrank on 2007-12-26
> **supernoob said:**
> I was wondering - could i change grub to load windows by default instead of Ubuntu (since I'm the only one who uses Ubuntu)

Hi and this link may help
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---


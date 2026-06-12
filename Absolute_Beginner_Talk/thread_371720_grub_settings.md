---
title: "grub settings"
date: 2007-02-27
forum: Absolute Beginner Talk
---

### Post by cacharreo on 2007-02-27
Hi:
How can I change the grub options: countdown time, default boot partition ....
thanks

---

### Post by taurus on 2007-02-27
It should be in /boot/grub/menu.lst.  Open a terminal, Applications -> Accessories -> Terminal, and edit it.
```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by Tomosaur on 2007-02-27
All of these settings can be altered by editing the grub config file. Hit at+f2, then type:
```

gksudo gedit /boot/grub/menu.lst

```

The file is documented, so you should be able to figure it out. Once you're done, save and exit, then reboot.

Alternatively, check the link in my sig.

---

### Post by Maestro23 on 2007-02-27
Great Grub doc: [http://users.bigpond.net.au/hermanzone/p15.htm#timer](http://users.bigpond.net.au/hermanzone/p15.htm#timer)

---


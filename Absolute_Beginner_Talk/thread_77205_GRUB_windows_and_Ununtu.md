---
title: "GRUB windows and Ununtu"
date: 2005-10-16
forum: Absolute Beginner Talk
---

### Post by natman on 2005-10-16
when i start up grub gives me the opion of windows or ununtu, if i wait for a bit it atumatically goes to ubuntu, can i change it so that windows is the default start up?
Thanks:

---

### Post by jnoreiko on 2005-10-16
Yes you can.
I don't have it in front of me, but you need to go into /boot and look for the grub menu file (google says it's /boot/grub/grub.conf).
There's a line in there that sets the default item in the boot menu. Just change that to what you want.

---

### Post by aysiu on 2005-10-16
Minus one from the number:

Default 0 (first entry)
Default 1 (second entry)
Default 2 (third entry)
and so on.

---

### Post by natman on 2005-10-16
Thanks for all the help, works fine now. 
Thanks:

---


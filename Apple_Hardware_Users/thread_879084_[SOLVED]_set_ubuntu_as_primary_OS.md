---
title: "[SOLVED] set ubuntu as primary OS"
date: 2008-08-03
forum: Apple Hardware Users
---

### Post by jeh0753 on 2008-08-03
Hi - I installed ubuntu on my macbook pro along with rEFIt, but I got rid of rEFIt, because I don't want a boot-up screen. I just want ubuntu to start when I turn on the computer. As of now, unless I hold down 'option' on the keyboard, mac osx starts by default. I tried to do it through the mac 'start-up disc' system preference, but as it doesn't know what an ext3 drive is, it would not allow me to set ubuntu as default. what do i do?

---

### Post by cyberdork33 on 2008-08-03
> **jeh0753 said:**
> Hi - I installed ubuntu on my macbook pro along with rEFIt, but I got rid of rEFIt, because I don't want a boot-up screen. I just want ubuntu to start when I turn on the computer. As of now, unless I hold down 'option' on the keyboard, mac osx starts by default. I tried to do it through the mac 'start-up disc' system preference, but as it doesn't know what an ext3 drive is, it would not allow me to set ubuntu as default. what do i do?
install refit again, and edit the config to boot into ubuntu by default.

---

### Post by jeh0753 on 2008-08-03
I did that, but I'd rather just boot right into the system, if there is any way to do that. I don't even want to go into a boot-up menu, just start up ubuntu when i try to power-up.

---

### Post by Victormd on 2008-08-03
Why don't you set ubuntu as default and set the timeout to 0? Then it would "skip" the boot menu.

---

### Post by kdb424 on 2008-08-03
Or do the Ubuntu only install, but if you do that, why own a mac?

---

### Post by cyberdork33 on 2008-08-03
> **Victormd said:**
> Why don't you set ubuntu as default and set the timeout to 0? Then it would "skip" the boot menu.
This is probably the best option, but I wouldn't completely skip it in case you needed something, just reduce it to like 1 sec.

You could also try blessing the Ubuntu partition, but I am unsure of all the effects that might have on your system.

---

### Post by jeh0753 on 2008-08-04
Hi- alright, in this case I suppose I'll just reinstall refit. I was just hoping for an alternative. If anyone has any other suggestions please share.. Otherwise thanks anyways, -Jake

---


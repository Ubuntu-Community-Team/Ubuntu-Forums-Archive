---
title: "Detailed Boot Sequence"
date: 2006-11-26
forum: Absolute Beginner Talk
---

### Post by jcknnm on 2006-11-26
Hi! I just switched from FC5 to Ubuntu today. I was wondering if it were possible to have the detailed list of services and things starting up like in Fedora. In FC5 there was a tab to expand to pick to show the services that it was going through to boot up. Does Ubuntu have something like this as well?

---

### Post by aysiu on 2006-11-26
No tab, unfortunately, but you can get rid of the bootsplash by editing /boot/grub/menu.lst and taking the word *splash* off the kernel you boot to.

---

### Post by taurus on 2006-11-26
Just remove the "quiet splash" in /boot/grub/menu.lst.  Then, you will see the old fashion way which service is starting...

Applications -> Accessories -> Terminal
```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by jerrykenny on 2006-11-26
Ubuntus a pest for installing a boot-up-fancy-splash-thingy 

at the boot prompt, press <e> for edit, repeat for the kernel . . . 

remove the word "splash" from the boot parameters

hit <enter>

then <b> for boot

---

### Post by jerrykenny on 2006-11-26
OK Taurus beat me to it, thats it, I'm off to bed,.

---

### Post by jcknnm on 2006-11-26
humm i suppose that works, hard to read but i suppose it works if i know what im looking for! thank you so much guys for the quick response! :)

---

### Post by taurus on 2006-11-26
Look for the line that starts with "kernel" like

```

title Ubuntu (2.17.18)
root (hd0,1)
kernel /boot/kernel-2.17.18 root=/dev/hda2 ro quiet splash
initrd /boot/initrd-2.17.18-img
blah
blah

```

---

### Post by taurus on 2006-11-26
> **jerrykenny said:**
> OK Taurus beat me to it, thats it, I'm off to bed,.
Don't you worry, I am off to a shower and it's bedtime too...  ;)

---


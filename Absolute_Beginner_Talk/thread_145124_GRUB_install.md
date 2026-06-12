---
title: "GRUB install"
date: 2006-03-15
forum: Absolute Beginner Talk
---

### Post by CookieOrc on 2006-03-15
I had to reinstall windows and it took out grub and I cannot get to my linux distro... so how can i reinstall it and get back into ubuntu?

---

### Post by Sef on 2006-03-15
Try this:

[https://wiki.ubuntu.com/phbc50/howtos/how-to_reinstall_grub?highlight=%28install%29%7C%28grub%29]("https://wiki.ubuntu.com/phbc50/howtos/how-to_reinstall_grub?highlight=%28install%29%7C%28grub%29")

---

### Post by mlind on 2006-03-15
You can use Ubuntu's cd to boot on your root partition.

then run ```
sudo grub-install /dev/???
```
where is the harddrive or device that's the first boot device on your bios.
Usually /dev/hda

---

### Post by CookieOrc on 2006-03-15
its on hda0

---

### Post by OBnascar on 2006-03-15
[QUOTE=CookieOrc]so how can i reinstall it and get back into ubuntu?[/QUOTE]

[**[COLOR="DarkOrange"]THIS[/COLOR]** ]("http://www.ubuntuforums.org/showthread.php?t=76652")was a good "how-to", easy and explained well I thought.

---


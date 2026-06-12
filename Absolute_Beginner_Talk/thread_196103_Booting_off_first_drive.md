---
title: "Booting off first drive?"
date: 2006-06-13
forum: Absolute Beginner Talk
---

### Post by fvs on 2006-06-13
I have been using fedora 5 with my master hd and I just installed Ubunto on my slave hd, I just want my master to have grub so that I can choose to load as I like,
I had my master grub working well with Debian as the slave, but Ubunto installed the grub to boot only, My question is can I go into /boot/menu in ubunto and comment it out and boot from the master grub? Sorry if it sounds mixed up.:confused:

---

### Post by confused57 on 2006-06-13
[QUOTE=fvs]I have been using fedora 5 with my master hd and I just installed Ubunto on my slave hd, I just want my master to have grub so that I can choose to load as I like,
I had my master grub working well with Debian as the slave, but Ubunto installed the grub to boot only, My question is can I go into /boot/menu in ubunto and comment it out and boot from the master grub? Sorry if it sounds mixed up.:confused:[/QUOTE]

Do you have a separate boot partition?  Ubuntu should have, by default, installed grub to the mbr of the master drive.

In Ubuntu, what does this show:

```
sudo gedit /boot/grub/menu.lst
```

Your fedora 5 should show up as "Other operating system" at the bottom of the grub menu.lst, if grub was installed to the master mbr.

---


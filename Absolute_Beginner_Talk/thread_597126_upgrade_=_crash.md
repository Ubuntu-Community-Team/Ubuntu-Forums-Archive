---
title: "upgrade = crash"
date: 2007-10-30
forum: Absolute Beginner Talk
---

### Post by johnnyw on 2007-10-30
Recently tried upgrading from dapper to 6.1 and crashed. Ive done now a fresh install of feisty and upgrade to gutsy and my graphical display is very crapped. Resolution is freaky and I cant even see the arrow from the mouse. how am I supossed to solve this??

I wont ever upgrade ubuntu again..I am really pissed off with ubuntu

---

### Post by Pumalite on 2007-10-30
Save data and do a clean install.

---

### Post by johnnyw on 2007-10-30
> **Pumalite said:**
> Save data and do a clean install.

no way.. it was supposed to be a secure install ( according to ubuntu.com)

---

### Post by taurus on 2007-10-30
> **johnnyw said:**
> Recently tried upgrading from dapper to 6.1 and crashed. Ive done now a fresh install of feisty and upgrade to gutsy and my graphical display is very crapped. Resolution is freaky and I cant even see the arrow from the mouse. how am I supossed to solve this??

I wont ever upgrade ubuntu again..I am really pissed off with ubuntu

What graphic card do you have?

---

### Post by johnnyw on 2007-10-30
radeon 9200 se ( agp)

---

### Post by taurus on 2007-10-30
Boot into recovery mode from GRUB menu and edit /etc/X11/xorg.conf

```
nano -Bw /etc/X11/xorg.conf
```
Scroll down until you get to the Section "Device".  Replace whatever Driver you have right now back to **vesa**.  Save it with <Ctrl>o and exit with <Ctrl>x.

Reboot and see if X is running properly now.

```
shutdown -r now
```

---

### Post by johnnyw on 2007-10-30
thx m8.. could solve it thanks to you

---

### Post by Pumalite on 2007-10-30
I learned something new. Thanks.

---


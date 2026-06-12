---
title: "How do you change the start up and shutdown loading screen thing?"
date: 2006-03-13
forum: Absolute Beginner Talk
---

### Post by davidk on 2006-03-13
Is there any way or any chance of changing the start up and shutdown?

---

### Post by davebradford on 2006-03-13
can you be more specific?

---

### Post by meborc on 2006-03-13
do you mean the splash image that shows brows ubuntu in the background when booting?

EDIT: for that try - [https://wiki.ubuntu.com/USplashCustomizationHowto](https://wiki.ubuntu.com/USplashCustomizationHowto)

---

### Post by mlind on 2006-03-13
And if you don't want splash image image at all, define *nosplash* option on grub
configuration file /boot/grub/menu.lst

```

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=nosplash

```

---


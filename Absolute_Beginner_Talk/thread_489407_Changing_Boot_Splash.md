---
title: "Changing Boot Splash"
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by jbraum on 2007-07-01
How do I  can my boot splash screen?

---

### Post by bodhi.zazen on 2007-07-01
Custom: [https://help.ubuntu.com/community/USplashCustomizationHowto](https://help.ubuntu.com/community/USplashCustomizationHowto)

Select: [http://doc.gwos.org/index.php/Different_usplash](http://doc.gwos.org/index.php/Different_usplash)

That or remove it ?

To remove it edit /boot/grub/menu.lst and remove the "splash" from the kernel line.

To make this permanent, edit these lines :

> ## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

To :

```
## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet
```

DO NOT REMOVE THE INITIAL # (These lines are formatted for GRUB configuration)

---

### Post by jbraum on 2007-07-01
Ok I got it.  I uninstalled Beryl - didn't really like it and now I get the following message when trying to set my windows preference.

Cannot start the preferences application for your window manager

Window manager "unknown" has not registered a configuration tool

---


---
title: "Need help restoring grub to original linux install..."
date: 2007-02-09
forum: Absolute Beginner Talk
---

### Post by encompass on 2007-02-09
I have installed feisty with no issues... but I want my originaly partition of edgy to be used to manage my grub settings.  How do I restore them so that my edgy stable install uses my grub install.  Not my unstable feitsy?

---

### Post by confused57 on 2007-02-09
You can reinstall grub, using the live cd:
[http://www.ubuntuforums.org/showthread.php?t=224351&highlight=grub+live+cd](http://www.ubuntuforums.org/showthread.php?t=224351&highlight=grub+live+cd)

What you can do is install Edgy's grub to (hd0) & install Feisty's grub to the root partition, e.g. setup (hd0,3) or whatever Feisty's root partition is located.

Add an entry to Edgy's grub to boot Feisty:

title   Feisty
rootnoverify  (hd0,3)
chainloader +1

---

### Post by bodhi.zazen on 2007-02-09
> **confused57 said:**
> You can reinstall grub, using the live cd:
[http://www.ubuntuforums.org/showthread.php?t=224351&highlight=grub+live+cd](http://www.ubuntuforums.org/showthread.php?t=224351&highlight=grub+live+cd)

What you can do is install Edgy's grub to (hd0) & install Feisty's grub to the root partition, e.g. setup (hd0,3) or whatever Feisty's root partition is located.

Add an entry to Edgy's grub to boot Feisty:

title   Feisty
rootnoverify  (hd0,3)
chainloader +1

Nice post :)

Next time leave something for me ...

Oh I know,

The advantage of chainloading fiesty is you will not have to manually update mneu.lst after kernel updates. You will however get two grub menus when you boot to fiesty ;)

To fix this, open Feisty /boot/grub/menu.lst and use these settings:

default 0
timeout 0

---

### Post by confused57 on 2007-02-09
> **bodhi.zazen said:**
> Nice post :)

Next time leave something for me ...

Oh I know,

The advantage of chainloading fiesty is you will not have to manually update mneu.lst after kernel updates. You will however get two grub menus when you boot to fiesty ;)

To fix this, open Feisty /boot/grub/menu.lst and use these settings:

default 0
timeout 0

Thanks...sorry, I was on a roll...your explanation for using chainloading was right on, I've made enough snafu's(mistakes) to find out the easiest ways to manage several distros on one computer.

---

### Post by encompass on 2007-02-11
Cool guys.... thanks for the advice... it fixed my issues... even better, it showed me how to better manage my installs.

---


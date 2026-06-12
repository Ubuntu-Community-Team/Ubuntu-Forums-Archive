---
title: "Nvidia troubles"
date: 2006-05-09
forum: Absolute Beginner Talk
---

### Post by Slavus on 2006-05-09
I want to get my real nvidia drivers up, since Vesa runs a slow interface.

I followed tseliot's HOWTO exactly, and suddenly I cant open Gnome anymore, it tries to change, goes black for a few seconds, and then goes back to the prompt.
Also, I cant switch back to the Vesa driver as it does the same thing now.. I have no desktop!

I checked the log and it tells me "Failed to load NVIDIA kernel module!" as well as "Screen(s) found, but none have usable configuration"

I tried both the regular and legacy drivers, produced the same result

Any suggestions?

---

### Post by Kvark on 2006-05-09
Sounds like you need to install the restricted(closed source) kernel modules, the package you need is named something similar to:
linux-restricted-modules-2.6.12-10-386

Check in the grub menu where you choose which OS to boot on startup to see which version of the kernel you are using and install the restricted modules package for that version.

Type this to see a list of the packages that deal with Nvidia kernel modules:
apt-cache search nvidia kernel

---

### Post by Slavus on 2006-05-09
sorry, this was a duplicate

---

### Post by Slavus on 2006-05-09
[QUOTE=Slavus]I found these two -- 

linux-restricted-modules-2.6.12-10-386 - Non-free Linux 2.6.12 modules on 386
linux-restricted-modules-2.6.12-10-386-nvidia-legacy - Non-free Linux 2.6.12 NVIDIA legacy module on 386

I used apt-get install and it said these are already the latest version. seems like I already have them? dunno but it still isnt working

---


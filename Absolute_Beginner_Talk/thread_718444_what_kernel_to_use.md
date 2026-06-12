---
title: "what kernel to use?"
date: 2008-03-08
forum: Absolute Beginner Talk
---

### Post by waspweb on 2008-03-08
Hi,
I just installed Ubuntu and after updating everything i get multiple kernel choices at in the grub. One that ends with 14, one 15 and one 16. Whats the difference and which one should i use? Also how can I remove the ones I dont use?

---

### Post by comandrei on 2008-03-08
Usually you should have only 1 kernel and the multiple choices are some boot parameters. But it's still the same kernel.

---

### Post by mikeyphi on 2008-03-08
> **waspweb said:**
> Hi,
I just installed Ubuntu and after updating everything i get multiple kernel choices at in the grub. One that ends with 14, one 15 and one 16. Whats the difference and which one should i use? Also how can I remove the ones I dont use?

Usually best to boot into the latest kernel. The difference is usually built-in updates for working with hardware.

You probably don't want to actually remove old ones unless you are tight on disk space but you can edit your grub list so that it only shows the last two kernels - gives you a choice if there is a problem!
Open a terminal and enter:
gksudo gedit /boot/grub/menu.lst

scroll down the menu until you find this section:
controls how many kernels should be put into the menu.lst

at the end of the section it says "how many=all"
change the all to 2 and save the file

---


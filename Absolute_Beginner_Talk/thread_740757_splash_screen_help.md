---
title: "splash screen help"
date: 2008-03-31
forum: Absolute Beginner Talk
---

### Post by New2Linux0319 on 2008-03-31
i want to download a nice cool splash screen. but dont understand the process.

first i used synaptic to get "gnome splash screen manager"
but when i opened it,, well, nothing.  i dont understand how to put my new splash in there.

so then i went and got lilo    and it says since its my first time using it i have to run
liloconfig(8)   and then execute   /sbin/lilo

i opened the "terminal" (text inputer)   and typed in liloconfig(8)   and nothing  (wrong command or something...)

any ideas?

---

### Post by erginemr on 2008-03-31
First of all, you are using GRUB as bootloader under Ubuntu, so forget about anything that says LILO, which is another boot loader used extensively in the past.

There are several splash screens. In the order of appearance:

(1) The boot splash screen that decorates the text-mode Grub boot menu.

(2) Ubuntu splash screen with Ubuntu logo and an orange progress bar.

(3) Gnome login screen, where you can input your user name and password.

(4) Gnome desktop splash screen, which has been disabled by default in Ubuntu 7.10.

So, which one are you referring to?

---


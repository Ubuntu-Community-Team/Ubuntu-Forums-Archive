---
title: "Is there a good online Grub tutor out there?"
date: 2007-01-13
forum: Absolute Beginner Talk
---

### Post by kexodusc on 2007-01-13
I installed Ubuntu and Kubuntu on my second machine.  Kubuntu first, then Ubunut - separate installs, separate partitions etc.

I don't seem to have the option to install Kubuntu when the Grub menu loads up - odd, I installed the two distro's in reverse order on my other machine and they both came up...anyhoo.

Just wunnerin' if there's a good, source for Grub out in cyberspace somewhere where I could learn how to add my Kubunutu install to the menu?

Thanks.

---

### Post by meng on 2007-01-13
wiki.ubuntu.com is good for tutorials:
[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

You realize that you don't NEED to have two partitions to run *buntu with GNOME and *buntu with KDE, don't you? You can have both installed on the same partition if you wish. Some folks do prefer them to be separate (myself I can't fathom why, but it's a matter of choice).

---

### Post by deanlinkous on 2007-01-13
look in the boot/grub of the kubuntu parition and open the menu.lst file and copy/paste the appropriate section to the menu.lst file that is on the Ubuntu parition....

---

### Post by kexodusc on 2007-01-14
> **deanlinkous said:**
> look in the boot/grub of the kubuntu parition and open the menu.lst file and copy/paste the appropriate section to the menu.lst file that is on the Ubuntu parition....

Thanks guys,

Meng, I did install the kubuntu-desktop over ubuntu on my machine at first - I prefer the separate installs just because it seems a wee bit smoother.  And it keeps 72 k-named apps out of the gnome menus :)

---


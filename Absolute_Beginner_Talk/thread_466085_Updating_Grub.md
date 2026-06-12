---
title: "Updating Grub"
date: 2007-06-06
forum: Absolute Beginner Talk
---

### Post by pardesi on 2007-06-06
suppose i changed something in the grub menu then how do i update it.

P.S.  this is an extension to pmy previous post** 'bug'** in which i couldn't get a workable anser

---

### Post by steeleyuk on 2007-06-06
sudo update-grub

---

### Post by pardesi on 2007-06-06
thanks

---

### Post by mahiyar on 2007-06-06
As far as I know update-grub regenerates the grub file by looking in the /boot folder for all instances of vmlinuz. If you have done any change in the menu.lst file there is no need to run any update script, the next time the computer boots the change menu.lst will come in to play.

---

### Post by sailor2001 on 2007-06-06
sudo gedit /boot/grub/menu.lst    You should find what you have changed here and could change it back

---

### Post by pardesi on 2007-06-06
actually i simply changed in the list and saved it but the problem persisited but after i updated the grub menu with the code everything went fine

---


---
title: "Grub acting up"
date: 2008-04-21
forum: Absolute Beginner Talk
---

### Post by saransk on 2008-04-21
I've never had any problem with GRUB until I started working with KDE.  I installed and uninstalled something so now instead either the Ubuntu or Kubuntu boot screens I get some text - almost like its looking for a suspended session - then it starts to load and goes to the Gutsy login screen.  I'm sure the answer is in the GRUB config file but When I look at it, I can't fins any reason for the "new' behavior.

Not sure where to look at this time - I may just wait for Hardy and do a clean install
any help is appreciated.

---

### Post by nge on 2008-04-21
probably you could try going into  suspend state then back in ?

---

### Post by bumanie on 2008-04-21
Please post output of 
> cat /boot/grub/menu.lst and > sudo fdisk -l That's if you can boot into ubuntu, otherwise try to locate the grub list via the live cd by going into file system and copying and pasting the grub list that way.

---


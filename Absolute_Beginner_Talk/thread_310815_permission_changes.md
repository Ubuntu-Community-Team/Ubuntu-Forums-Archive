---
title: "permission changes"
date: 2006-12-01
forum: Absolute Beginner Talk
---

### Post by sdg on 2006-12-01
Hi, real new here at Ubuntu. I am trying to edit the menu.lst config file so I can change default grub bootup to Windows for my wife. I like Ubuntu alot but want to learn it to show my wife later. gecit will not let me save the config file since I do not have root acces which I know is through sudo but I do not know how to use all of this together to lighten up gedit so that I can change the menu.lst config file. Help please so that my house will again be at peace. Thanks for any advice/instructions.:D

---

### Post by mushroom on 2006-12-01
alt+f2

```
gksudo gedit
```

---

### Post by Chinkostu on 2006-12-01
in terminal

```
Sudo gedit /boot/grub/menu.lst
```

remember to remove saveddefault from the ubuntu entry :)

---

### Post by sdg on 2006-12-01
Um does this mean when I type this code in terminal it will call up the config file for editing?? If so How do I save the changes?? Thanks again

---

### Post by mushroom on 2006-12-01
It will save normally, because you're running it as root, and thus have root permissions.

---

### Post by sdg on 2006-12-01
Thanks all I will attempt this again. Smokin repy speed!!!

---

### Post by ewl1217 on 2006-12-01
Before you edit it, you should make a backup (that is, if you haven't already).
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
```

---

### Post by sdg on 2006-12-01
Yes I did Thanks anyway. If I have to re-instate the backup as .lst 
Do I do that in terminal too  or just sudo gedit somehow??

---

### Post by mushroom on 2006-12-01
sudo mv /boot/grub/menu.lst.backup /boot/grub/menu.lst

---

### Post by sdg on 2006-12-01
Thanks again. One more question, I have 1.5mbs LAN connection to internet. It smokes when firefox is accessing links but has a long lag between actual accessing moments . In other words I click a link and ther is a long pause before firefox trys anything. This lag is not present on XP. Do you think it is reconnecting each time or what??

---

### Post by mushroom on 2006-12-01
It's a Firefox quirk. I recommend Epiphany, which uses the same rendering engine as Firefox and it uses many of its extensions.

```
sudo apt-get install epiphany-browser epiphany-extensions
```

---

### Post by sdg on 2006-12-01
Ok Thanks . I will try

---


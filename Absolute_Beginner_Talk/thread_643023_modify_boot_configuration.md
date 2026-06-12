---
title: "modify boot configuration"
date: 2007-12-17
forum: Absolute Beginner Talk
---

### Post by lloydlee on 2007-12-17
hi,

i have successfully installed ubuntu in my laptop with win xp. it is running as it should.

whenever i boot, the boot options are displayed for me to choose. after a period of time it boots ubuntu as default.

how can i configure the boot sequence to remove the time limit to choose. i want the boot sequence to require me to choose before it proceeds. if i have not yet chosen ubuntu or win xp, then it will just remain as is and will not proceed to boot.

thanks,

lloyd

---

### Post by skrribble on 2007-12-17
you have to edit your /boot/grub/menu,lst file.  Open a terminal and type:
```
gksudo gedit /boot/grub/menu.lst
```
from what I can tell, you should just be able to comment out the line that says timeout and then a number

---

### Post by Lord_Dicranius on 2007-12-17
I think commenting out (adding a "#" to the beginning of the line) the "timeout=" line in /boot/grub/grub.conf will make it sit until you choose an option.

*EDIT*
skrribble beat me to it.  And I always get confused which file it is: grub.conf or menu.lst :-P

---

### Post by eilu on 2007-12-17
I would like to add, make a backup of your menu.lst before you change anything, in case some unforeseen hiccup occurs

---

### Post by lloydlee on 2007-12-18
Thanks for all your help, it works as i wanted now:)

---


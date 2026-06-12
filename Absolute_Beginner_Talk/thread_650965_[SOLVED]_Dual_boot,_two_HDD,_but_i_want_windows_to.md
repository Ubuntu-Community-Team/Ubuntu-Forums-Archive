---
title: "[SOLVED] Dual boot, two HDD, but i want windows to be default"
date: 2007-12-27
forum: Absolute Beginner Talk
---

### Post by iamclueless on 2007-12-27
ok ive been dual booting for two weeks now with Xubuntu giving you 7 seconds to decide if you want to run Windows

is there a way i can reverse this?  Can the boot loader be made to run WIndows as the first choice?  i imagine ill be gediting the menu.lst file

thanks

---

### Post by bodhi.zazen on 2007-12-27
Yes, just use gedit 

```
gksu gedit /boot/grub/menu.lst
```

There is a line, "default         0"

Grub starts numbering with 0, so you can either put your windows entry above your ubuntu entries or change the default to 2 (assuming 2 entries for ubuntu and the third is windows).

If you go the second route you will need to update the number if you install a new kernel

---

### Post by iamclueless on 2007-12-27
so simply paste this (move from the bottom, above the 3 other boot options)?

title Windows XP
root (hd1,0)
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

above the ubuntu stuff?

---

### Post by bodhi.zazen on 2007-12-27
Yes, that should do it

---

### Post by iamclueless on 2007-12-27
excellent! just did it now

thanks mate

---

### Post by meierfra on 2007-12-27
The solutions you just did works.  But please move your windows item above the line:

### BEGIN AUTOMAGIC KERNELS LIST

Otherwise your   windows item will disappear after the next kernel update. 
Everything between 

### BEGIN AUTOMAGIC KERNELS LIST

        and 

### END DEBIAN AUTOMAGIC KERNELS LIST

gets  rewritten during kernel update.

You can  test this: Just run

```
sudo  update-grub
```

in a terminal and you will see that the windows item is  gone. (assuming it was below ### BEGIN AUTOMAGIC KERNELS LIST.)

---


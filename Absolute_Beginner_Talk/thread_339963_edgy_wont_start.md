---
title: "edgy wont start"
date: 2007-01-16
forum: Absolute Beginner Talk
---

### Post by jinxjinx on 2007-01-16
i just installed edgy and it worked fine then i restarted and i got "GRUB loading, Error 15"
i tried reinstalling twice but no avail....

someone please help.

---

### Post by jinxjinx on 2007-01-16
nm i fixed it. 

for some reason it was trying to boot ubuntu from my other hard disk! so i had to edit the menu.lst

---

### Post by jinxjinx on 2007-01-16
nooo!! its broken again. i think some program undid my changes 

i edited /usr/share/doc/grub/examples/menu.lst 

and 
the code

#for booting GNU/Linux
title GNU/Linux
root (hd1, 0)
kernel /vmlinuz root=/dev/hdb1


is wrong!
my rood is actually hd0!
vmlilnuz is in /boot/vmlinuz

when i changed it the first time it booted, but now every time i change it it goes back to this and wont start

some one have any idea whats going on?

---

### Post by riven0 on 2007-01-16
Don't edit /usr/share/doc/grub/examples/menu.lst! That's not the correct one. What you're looking for is /boot/grub/menu.list. That's the one you want to edit. So:

> sudo gedit /boot/grub/menu.list

Put the correct changes in there and you should be fine.

---


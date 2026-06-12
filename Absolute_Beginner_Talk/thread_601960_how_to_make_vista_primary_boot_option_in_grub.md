---
title: "how to make vista primary boot option in grub?"
date: 2007-11-03
forum: Absolute Beginner Talk
---

### Post by littleasian on 2007-11-03
hey guys.

im wondering, how can i configure grub to make it so it boots vista by default if i dont touch anything.

right now, its still set in its default form, so upon turning on my computer i see:

1.  Ubuntu 7.10
2.  Ubuntu 7.10 kernal
3.  Ubuntu 7.10 something else
4.  Vista/Longhorn

I want to make it so that the default option is vista, instead of ubuntu.

how do i do this?

thanks!!

---

### Post by carlosjuero on 2007-11-03
You have to edit the GRUB boot menu located at /boot/grub/menu.lst

Heres a site with a quick rundown: [http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)

---

### Post by Pumalite on 2007-11-03
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by littleasian on 2007-11-03
i dont quite understand what the "paramters" are in the website link.

can someone give me to them in more "layman" terms?  im a real newbie at linux...

---

### Post by ddrichardson on 2007-11-03
If you look in /boot/grub/menu.lst then there is an entry that says default=0, change it to default=3 (in your case). Open a terminal and type:
```
gksudo gedit /boot/grub/menu.lst
```
Change the 0 to a 3 and save.

---


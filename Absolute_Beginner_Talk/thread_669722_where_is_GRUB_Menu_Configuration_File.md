---
title: "where is GRUB Menu Configuration File?"
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by taekr on 2008-01-16
gksudo gedit /boot/grub/menu.lst

gives me a blank... 

It's empty which shouldn't be!  I do dual boot

---

### Post by lgambett on 2008-01-16
check the spelling...

verify issuing the command

ls /boot/grub/menu.lst

---

### Post by zipperback on 2008-01-16
> **taekr said:**
> gksudo gedit /boot/grub/menu.lst

gives me a blank... 

It's empty which shouldn't be!  I do dual boot

issue the following:

```

less /boot/grub/menu.lst

```

That should display the file. If it does not, and the file appears blank, then you've done something which has wiped it.

Be sure you are typing a lowercase L and not a numeral 1 for menu.lst

-zipperback
:popcorn:

---

### Post by benanzo on 2008-01-16
You can regenerate GRUB's config file by doing:
```
sudo update-grub
```

That will re-read the partition table, look for bootable systems and write the generic config back to **/boot/grub/menu.lst**

---

### Post by p_quarles on 2008-01-16
> **lgambett said:**
> check the spelling...

verify issuing the command

ls /boot/grub/menu.lst
+1. A very common mistake is to type the "grub.lst" with the numeral one, rather than with a lower-case L.

---

### Post by bodhi.zazen on 2008-01-16
Other potential problem is you open the file as a non-root user

nano /boot/grub/menu.lst

will be blank

---

### Post by OffAxis on 2008-01-16
```
ls /boot/grub/m
```
and, without hitting the 'Enter' key, press 'Tab' twice. It'll display the contents of the folder that start with 'm'

---


---
title: "grub is hard drive threatning!!!!!"
date: 2008-01-15
forum: Absolute Beginner Talk
---

### Post by chips24 on 2008-01-15
i have a vista menu on my grub loader to wipe off the hard drive and start vista new, this is treatening for all my information, need to hide a lot of options on grub!!!!!!

---

### Post by Joeb454 on 2008-01-15
run

```
gksu gedit /boot/grub/menu.lst
```

and then comment out the things you don't want (to comment out, put a # at the start of the line)

Hope this helps, and don't forget to back up menu.lst first

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak
```

---

### Post by aidanr on 2008-01-15
Never heard of that before, but anyway you can remove it from the menu.lst
```
gksudo gedit /boot/grub/menu.lst
```

Edit: too slow :)

---

### Post by chips24 on 2008-02-04
the original operating system has a thing where you can revert to factory condition.

---

### Post by LaRoza on 2008-02-04
> **chips24 said:**
> the original operating system has a thing where you can revert to factory condition.

That is actually on a different partition, and is a different operating system (usually). It is added to Grub sometimes, and you can hide it by commenting it out it line.

---


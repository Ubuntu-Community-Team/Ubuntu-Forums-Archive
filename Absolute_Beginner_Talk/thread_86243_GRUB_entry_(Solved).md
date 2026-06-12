---
title: "GRUB entry (Solved)"
date: 2005-11-04
forum: Absolute Beginner Talk
---

### Post by Griff on 2005-11-04
Getting ready to dualboot another PC.  This one has only one NTFS partition, but 2 XP boot options on the grub.  How do i delete one of these?  The one i need to delete is from an old install that is corrupted beyond repair.

---

### Post by aysiu on 2005-11-04
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
sudo nano /boot/grub/menu.lst
```
Find the entry you don't want and put ## signs in front of it.
Then
Control-X
Y
Enter

---

### Post by Griff on 2005-11-04
And this will work from the terminal of a live cd?

---

### Post by linbetwin on 2005-11-04
Does the PC have Ubuntu installed on the hard drive? If it does, why use the LiveCD? If it doesn't, what GRUB are you talking about?

---

### Post by Griff on 2005-11-04
Entry gone.  Thanks guys.

---


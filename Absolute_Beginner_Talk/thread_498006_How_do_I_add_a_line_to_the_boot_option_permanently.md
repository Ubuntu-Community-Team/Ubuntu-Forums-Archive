---
title: "How do I add a line to the boot option permanently?"
date: 2007-07-10
forum: Absolute Beginner Talk
---

### Post by randytuggle on 2007-07-10
If I want to add an option to the boot options such as pci=noacpi, how would I add that option so that I wouldn't have to manually type it at each boot sequence? I am having hard drive errors such as "hdb: status error: status=0x50" and read on one site that adding such an option would help the problem.

---

### Post by glennric on 2007-07-10
Add the option to the end of the kernel line in the file /boot/grub/menu.lst

---

### Post by randytuggle on 2007-07-10
the system won't let me save the file - only SAVE AS. How do I save it?

---

### Post by macogw on 2007-07-10
sudo gedit /boot/grub/menu.lst

go to the line that says 
# defoptions
add your command to the end of the line and save it

sudo update-grub

---

### Post by randytuggle on 2007-07-10
thanks!

---


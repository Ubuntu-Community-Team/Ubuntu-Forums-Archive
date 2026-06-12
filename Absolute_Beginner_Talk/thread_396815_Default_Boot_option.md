---
title: "Default Boot option"
date: 2007-03-29
forum: Absolute Beginner Talk
---

### Post by pc_savant on 2007-03-29
I am fairly new to linux and the installation went perfectly!  Is there any way I can make Windows XP as the default option in the boot loader?

---

### Post by halitech on 2007-03-29
search is your friend :)

[http://www.ubuntuforums.org/showthread.php?t=396520&highlight=boot+grub]("http://www.ubuntuforums.org/showthread.php?t=396520&highlight=boot+grub")

```

sudo nano /boot/grub/menu.lst

```

change default from 0 to whatever option windows is on your list

---

### Post by pc_savant on 2007-03-31
Thanks Halitech,
Once I change the booting option, I can't seem to save that.  Any particular way of doing it?

Regards

---

### Post by halitech on 2007-03-31
CTRL-O will save the file then Ctrl-X to exit and go back to the terminal.

---

### Post by pc_savant on 2007-04-01
Thanks Halitech,

Managed to do it this time!!! Just Perfect:)

---


---
title: "Screen shot"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by captgadget on 2007-06-20
I see a lot of post where some one takes a picture of their say grub menu and I can use the scroll bars in their posts. How do you do that so I could post my grub menu.lst?

---

### Post by Inxsible on 2007-06-20
> **captgadget said:**
> I see a lot of post where some one takes a picture of their say grub menu and I can use the scroll bars in their posts. How do you do that so I could post my grub menu.lst?
 
you can copy paste it between [code ] and [/code ] without the spaces in the square brackets. Its not a picture of the grub menu. they simply copy paste the text

---

### Post by Golyadkin on 2007-06-20
If you want to copy paste from the terminal, don't press Control-C but select the text, right click and select "Copy". Control-C is a shortcut to killl a running program in a terminal.

---

### Post by captgadget on 2007-06-20
If it's a really long menu, like my grub menu, how do I capture the whole thing.

That would the results of sudo nano /boot/grub/menu.lst

---

### Post by vegetable on 2007-06-20
you could also copy/paste from the terminal using ctrl-shift- c/v

---

### Post by Golyadkin on 2007-06-20
> **captgadget said:**
> If it's a really long menu, like my grub menu, how do I capture the whole thing.

That would the results of sudo nano /boot/grub/menu.lst

Simply redirect the console output to a file:
> 
sudo cat /boot/grub/menu.lst > ~/grubmenu.txt


Now you have a textfile in your homedir which you can open and copy paste the contents from into a forum post.

---

### Post by Inxsible on 2007-06-20
of instead of using nano, you can use a graphical editor like gedit...

```
gksudo gedit /boot/grub/menu.lst
```

---


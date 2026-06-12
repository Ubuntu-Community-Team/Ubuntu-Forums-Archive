---
title: "Grub Problem.."
date: 2006-07-11
forum: Absolute Beginner Talk
---

### Post by cyberlite on 2006-07-11
I have a question since today and after an update, I get 3 ways to (Boot in grab) to ubuntu.. all the same  How can I delete the 2???

P.S.The seconde boot was criated when I installed Kubuntu, the 3rd today after an update.

---

### Post by annda on 2006-07-11
you need to edit the file /boot/grub/menu.lst

- just delete duplicate entries, leaving only one

---

### Post by Swab on 2006-07-11
> **annda said:**
> you need to edit the file /boot/grub/menu.lst

- just delete duplicate entries, leaving only one

and then do "sudo grub-install hd0" or something similar :)

---

### Post by cyberlite on 2006-07-11
Edit with what progam??

---

### Post by Emceay on 2006-07-11
From your terminal prompt.
cd boot/grub/
sudo gedit menu.lst
I think those commands should bring up the menu list. This is my second day so I may have missed a directory or something :D

---

### Post by Swab on 2006-07-11
> **cyberlite said:**
> Edit with what progam??


Open up the terminal... then type

```

sudo su   (enter your password)
gedit /boot/grub/menu.lst

```

make the changes you need then save it and close gedit.. back to the terminal window...

```

grub-install hd0

```

---

### Post by FenrisAbraxas on 2006-07-11
> **Swab said:**
> Open up the terminal... then type

```

sudo su   (enter your password)
gedit /boot/grub/menu.lst

```

make the changes you need then save it and close gedit.. back to the terminal window...

```

grub-install hd0

```

You don't need the "grub install hd0" part... grub is already installed and menu.lst is just a config file :S you can add remove, edit or whatever without have to install it again :)

---

### Post by cyberlite on 2006-07-12
Thx man, Great help........... (solved)\\:D/

---


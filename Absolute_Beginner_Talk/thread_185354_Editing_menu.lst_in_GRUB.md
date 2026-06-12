---
title: "Editing menu.lst in GRUB"
date: 2006-05-31
forum: Absolute Beginner Talk
---

### Post by roncg41677 on 2006-05-31
I am trying to change the default OS in GRUB to XP, but I don't know how to enter root to use the text editor on the file. I've brought up the terminal and typed "su root", and it asks for a password. When I type nothing happens on screen. I tried the password anyway and hit "enter" and got an "authentication failed" message. 

I've just installed 5.1 to my hard drive, and I'm still pretty new at this. Thanks for you help (again:))

---

### Post by aysiu on 2006-05-31
[https://wiki.ubuntu.com/GrubHowto/ChangeDefaultOS](https://wiki.ubuntu.com/GrubHowto/ChangeDefaultOS)

---

### Post by roncg41677 on 2006-05-31
Thanks Aysiu! That looks like it worked. I forgot to check the Wiki.

---

### Post by roncg41677 on 2006-05-31
Can you explain to me what happened with those commands in the link? What did I actually do?

---

### Post by aysiu on 2006-05-31
*default #* is the entry number that's the default.

The numbering starts at 0.

So if you have these entries, these will be the numbers:

0 Ubuntu
1 Recovery mode
2 Memtest
3 Other operating systems label
4 Windows

The default default number is 0 (Ubuntu). If you change it to 4, Windows will be the default.

---

### Post by roncg41677 on 2006-05-31
> 
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup 
sudo gedit /boot/grub/menu.lst


I'm sorry, I meant these commands, not the menu.lst. What is this telling the computer to do?

---

### Post by aysiu on 2006-05-31
[QUOTE=roncg41677]I'm sorry, I meant these commands, not the menu.lst. What is this telling the computer to do?[/QUOTE] The first one copies the menu.lst file to a backup in case you screw up the file.

The second command lets you edit the file.

---


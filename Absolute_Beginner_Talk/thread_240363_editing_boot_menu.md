---
title: "editing boot menu"
date: 2006-08-20
forum: Absolute Beginner Talk
---

### Post by KGH on 2006-08-20
I changed the drives in the boot menu but I can't save the file. It says I don't have permission. How do I change this so I don't have to edit the boot file everytime I restart the computer.

KGH](*,)

---

### Post by zxee on 2006-08-20
Are you asking about /boot/grub/menu.lst?
To edit anything, that's outside your home/user directory you need to be root so open the text editor of your choice with sudo e.g.
sudo nano /boot/grub/menu.lst

---

### Post by kinematic on 2006-08-20
i assume that you have root rights?
if so open a terminal and type gksudo gedit /boot/grub/menu.lst and that will let you edit your menu list as root and enable you to save the changes.

---

### Post by KGH on 2006-08-20
I typed "gksudo gedit /boot/grub/menu.lst", entered my password and nothing happened. I retyped "gksudo gedit /boot/grub/menu.lst" and I get file not found. Do I need to change directory or something?

---

### Post by LeslieL on 2006-08-20
I copied your command "gksudo gedit...." into my console and had no problem editing menu.lst. So you're doing it right, if that's what you actually typed. Try again? You're on the right track, anyway.

---

### Post by bodhi.zazen on 2006-08-20
Perhaps you deleted /boot/grub/menu.1st?

What do you get when you type
```
ls /boot/grub/ | grep menu
```

You should see
```
menu.lst
```

If you have not deleted menu.1st try
```
su nano /boot/grub/menu.1st
```

To exit nano -> Ctrl-X -> Y to save your edit, N to exit without saving.

---

### Post by akniss on 2006-08-20
> **bodhi.zazen said:**
> Perhaps you deleted /boot/grub/menu.1st?

What do you get when you type
```
ls /boot/grub/ | grep menu
```

You should see
```
menu.lst
```

If you have not deleted menu.1st try
```
su nano /boot/grub/menu.1st
```

To exit nano -> Ctrl-X -> Y to save your edit, N to exit without saving.

Make sure you are typing menu.lst with an l as in Love, not the number 1 as was shown in the above post.

---

### Post by bodhi.zazen on 2006-08-20
Oops, sorry for the typo.

---

### Post by KGH on 2006-08-21
I guess it was my typing. I copied & pasted gksudo gedit... & edited my menu file. After making my changes & saving the file I typed the same line & it work just as when I cut & pasted.:-D 

All I got using the line su nano /boot/grub/menu.lst was unknown id: nano. Care to take a guess at why?

BTW the last time I used command line was over 16 years ago on my Amiga 500.

---

### Post by Malac on 2006-08-21
You can't su nano.
Simply put, su is a command to raise your privileges for the session in the terminal so you don't have to keep typing sudo.

---

### Post by akniss on 2006-08-21
> **KGH said:**
> I guess it was my typing. I copied & pasted gksudo gedit... & edited my menu file. After making my changes & saving the file I typed the same line & it work just as when I cut & pasted.:-D 

All I got using the line su nano /boot/grub/menu.lst was unknown id: nano. Care to take a guess at why?

BTW the last time I used command line was over 16 years ago on my Amiga 500.

instead, use
```
sudo nano /boot/grub/menu.lst
```

---


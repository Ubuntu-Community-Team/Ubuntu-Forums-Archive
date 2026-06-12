---
title: "GRUB menu"
date: 2007-02-11
forum: Absolute Beginner Talk
---

### Post by aalr1986 on 2007-02-11
hi, this is a quick question
I just wanna change the order in the GRUB list, cause the first one is the UBUNTU one, but instead I wanna put my WXP first.
How do I do that?

---

### Post by meng on 2007-02-11
sudo nano -B /boot/grub/menu.lst

My suggestion is, rather than change the order of entries, to set the line which reads
default 0

to read 
default {other number}

where the other number refers to the stanza containing Windows XP. Count from the top 0, 1, 2, etc.

---

### Post by nickoli_02 on 2007-02-11
```
gksudo gedit /boot/grub/menu.lst
```

To change the boot priority in grub, you want to change the "default 0" option to "default n" where XP is the nth menu item in the list.

The top of menu.lst there are various options with an explanation of what each option does. I'd recommend reading through them, some you may find useful :)

---

### Post by aalr1986 on 2007-02-11
Aight, I get it now. And thanks, I appreciate it.
But, my question now would be, where do I type that code?

---

### Post by meng on 2007-02-11
Open a Terminal
Applications > Accessories > Terminal

---

### Post by aalr1986 on 2007-02-11
> **meng said:**
> Open a Terminal
Applications > Accessories > Terminal

ok, I open Terminal, and then what? I mean, I opened the file and everything, but it won't let me change it, so you're telling me I open Terminal, type all that, and then what?!?!?

---

### Post by meng on 2007-02-11
1. open terminal
2. sudo nano (etc)
3. make the changes
4. ctrl-x and save

(Edit 2b: in response to sudo nano ... you type your user password and press enter)

---

### Post by y-lee on 2007-02-11
You can find documentation on GRUB in several different formats at [GNU GRUB Manual]("http://www.gnu.org/software/grub/manual/"). A post here also gives a [GrubEd script ]("http://www.ubuntuforums.org/showthread.php?t=228104")which gives users a nice GUI to alter their grub settings. And another program to do the same can be found at [Configure grub and usplash settings using Simple GUI Interface in Ubuntu]("http://www.debianadmin.com/configure-grub-and-usplash-settings-using-simple-gui-interface-in-ubuntu.html"). Either of these two allow for alot of tweaking of grub atho simple editing of the menu.lst file is perhaps the easiest for what you desire. Also perhaps of interest is the [Super Grub Disk]("http://supergrub.forjamari.linex.org/?section=home") which can fix grub and boot problems in case of disaster!!

---

### Post by aalr1986 on 2007-02-11
thanks for the help! It worked!! Thanks!

---


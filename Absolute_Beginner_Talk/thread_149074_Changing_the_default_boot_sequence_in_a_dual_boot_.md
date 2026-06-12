---
title: "Changing the default boot sequence in a dual boot system"
date: 2006-03-23
forum: Absolute Beginner Talk
---

### Post by Vincent1 on 2006-03-23
Can someone please help...i need to know what's the easiest way to change the default boot sequence.

---

### Post by dermotti on 2006-03-23
sudo gedit /boot/grub/menu.list

just cut n paste your operating systems in what ever order you want.

make a backup first tho

---

### Post by Luke on 2006-03-23
[https://wiki.ubuntu.com/GrubHowto/ChangeDefaultOS](https://wiki.ubuntu.com/GrubHowto/ChangeDefaultOS)

---

### Post by petervk on 2006-03-23
Be careful, if you mess up the menu.list file you can cause your computer to not  be able to boot.

A more careful method of doing this is...

Crap. Luke beat me too it. Follow the wiki link.

---

### Post by aysiu on 2006-03-23
[QUOTE=petervk]
A more careful method of doing this is...[/QUOTE] Well, I would say a careful way to do it is to

1. back up any configuration file before editing it
2. always have a live CD handy

---


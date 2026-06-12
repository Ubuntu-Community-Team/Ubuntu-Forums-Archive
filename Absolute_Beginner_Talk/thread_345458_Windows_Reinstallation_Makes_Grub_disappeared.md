---
title: "Windows Reinstallation Makes Grub disappeared"
date: 2007-01-24
forum: Absolute Beginner Talk
---

### Post by itisgood on 2007-01-24
Hi everyone:

I installed Windows XP and Ubuntu dual boot long ago, it works fine.

But recently, in the case my windows XP has been infected by a serious virus, I reinstalled the windows XP. 

the reinstalled Windows XP works fine, but the problem is that, now when the computer is booted, it automatically boot to windows XP without any choice, it used to run grub first, but now it seems that the installation of XP has replace the grub by its own boot program. 
How can I fix this problem?

thx

---

### Post by youthforlinux on 2007-01-24
This should work [https://wiki.ubuntu.com/phbc50/howtos/how-to_reinstall_grub?highlight=%28reinstall%29]("https://wiki.ubuntu.com/phbc50/howtos/how-to_reinstall_grub?highlight=%28reinstall%29")

---

### Post by frotzed on 2007-01-24
When you reinstalled Windows did you reformat your hard disk?

---

### Post by itisgood on 2007-01-24
I didnot format anything, the linux is still there, I just cannot enter it ....hehe

---

### Post by jvc26 on 2007-01-24
> **frotzed said:**
> When you reinstalled Windows did you reformat your hard disk?

Nope - its the fact that Windows wipes the MBR and puts its own windows bootloader onto it rather than GRUB, and hence you have to reinstall GRUB to retrieve it :) (Which I believe a post ^^ had a link to)
Il

---

### Post by bichopro on 2007-01-24
[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

very usefull :)

---


---
title: "using ttf fonts"
date: 2006-07-11
forum: Absolute Beginner Talk
---

### Post by DanWan on 2006-07-11
In edubuntu: is there a simple way to use MAc fonts I downloaded and unzipped in my desktop.

Trying to place them in my system files tells me I have no [riviledges to do so.

THe help guide does not help as there is no security menu in the System>Administration combo nor anthing like YAST


I am lost what to do?

---

### Post by digby on 2006-07-11
You need to put those fonts in one of a couple of different places: either /usr/share/fonts or ~/.fonts - then you have to run```
sudo fc-cache -fv
```This will rebuild your font list so that other applications will find it.

As to your permissions/priviledges issue, the directory you were trying to access is probably owned by root.  To copy files into it, therefore, you need to use sudo (or run 'gksudo nautilus' to do it w/ the gui).

---

### Post by DanWan on 2006-07-13
Thanks so much ... I am very new to Linux and after about one month of testing it on my Vaio VGNt27 that the problem is the 'administration rule' leading to constant typing Linux requires.

Do you know if there are ways to use linux (even risking to ruin the system) without gooing through the different routines of 'permissions'


Or is there a command allowing me to temporarily disable the system requests for root and simply allow me to drag and drop things where needed (such as fonts in this case)

I understand the linux community is a close comunity mainly developpers and or computer geeks, but if any of you is realkly thinking to remove Windows and it's unfair philosophical threat to people's independence and privacy, then you should agree on some simple but necessary tasks as: 

Installer explaining what it does: I search for something (ie blue tooth) find it in Synaptic, but then how to get it to work is always complex and frustrating unless you're really parts of the .nix community at large.

---


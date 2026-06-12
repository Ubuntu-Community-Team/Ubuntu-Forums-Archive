---
title: "give me a solution"
date: 2006-06-05
forum: Absolute Beginner Talk
---

### Post by gordonyb0 on 2006-06-05
Wow,i'm facing to a big trouble.
I cannot connect to internet in Ubuntu and have not got cdrom.
as a result, i'm not able to install any software including GCC and GDB which i need for my design eagerly.
i'm wondering if i can download the necessary ware and install them mannually?
There are too much dependencies,aren't there?
so what's the solutiong to my question?:-k

---

### Post by nalmeth on 2006-06-05
[quote=gordonyb0]Wow,i'm facing to a big trouble.
I cannot connect to internet in Ubuntu and have not got cdrom.
as a result, i'm not able to install any software including GCC and GDB which i need for my design eagerly.
i'm wondering if i can download the necessary ware and install them mannually?
There are too much dependencies,aren't there?
so what's the solutiong to my question?:-k[/quote]

need some more info from you first

Are you using a wireless or wired internet connection?
Do you have another computer with ready connection, possibly dual-booting with windows?

---

### Post by gordonyb0 on 2006-06-05
none of them.
I'm having one computer with no connectiong with the internet](*,)

---

### Post by nalmeth on 2006-06-05
If you can find the [ubuntu packages]("http://packages.ubuntu.com/") on another computer outside your home, and burn them onto a CD / USB memory, you can install them manually. Copy them to your harddrive from a CD, say to your /home, in a folder called packages. Also, check the package information for extra dependencies. 

You can use the graphical .deb installer to install them. Double-click the files, or right-click and select the deb installer if that doesn't work.

Alternatively, in the terminal, you could change to this packages directory, and install them all with one command:

cd ~/packages
sudo dpkg -i *.deb

---

### Post by gordonyb0 on 2006-06-05
Thanx a lot

---


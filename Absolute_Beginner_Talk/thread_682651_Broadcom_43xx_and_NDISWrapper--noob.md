---
title: "Broadcom 43xx and NDISWrapper--noob"
date: 2008-01-30
forum: Absolute Beginner Talk
---

### Post by tylermc on 2008-01-30
I have read through a lot of the other posts related to this topic and I can't find an answer!

Here are the problems I am having:

I have a Gateway M520XL notebook with a Broadcom 43xx wireless card in it. I can't enable it because I don't have the drivers installed. I have the drivers saved on a disk (from when I used Windows) and I am attempting to use NDISwrapper to install them and get the wireless working. I don't quite understand packages yet and I am unable to load a graphical interface (if there is one) for NDISwrapper. I attempted to use the Terminal to install the drivers, but again, I don't know quite how to do it. 

My questions:
1) How do I use NDISwrapper either graphically or through the terminal?
2) When I install a package through Synaptics, how do I get the program to run? Where is it located at? (I'm used to Windows!)

That's all for now! Thanks!

---

### Post by luisromangz on 2008-01-30
1. In the ndiswrapper website they explain how to install the wireless drivers using it.
2. When you install a package that contains a program, if it is a graphical application it should install a menu item along the program itself, if it is a command line application, it will just install the program. You can always check what files a package have installed in the package's properties dialog.

---

### Post by jan quark on 2008-01-30
i would run it via the fwcutter
like I have explained here

[http://janquark.fatfreehost.com/tutorial1.html](http://janquark.fatfreehost.com/tutorial1.html)

the ndiswrapper method never have worked for me ( have a 4311 broadcom)
and believe me I have tried many many guides and howtos

---

### Post by mikeyphi on 2008-01-30
Go with post #3. Ubuntu now has support for Broadcom.....don't use ndiswrapper if at all possible!

---


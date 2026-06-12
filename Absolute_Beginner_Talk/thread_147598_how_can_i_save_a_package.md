---
title: "how can i save a package??"
date: 2006-03-20
forum: Absolute Beginner Talk
---

### Post by axl000 on 2006-03-20
hi, first, sorry for my english.
i want to know how to save a package to a  external drive (usb pendrive for example) and then when i install ubuntu, install this package from the external drive.

i need this for install ubuntu with xubuntu-desktop in a computer with no internet conection, and i cant update online (i know i can try to download xubuntu and intall it directly, but i dont want to download it, i think its no necessary) 

please teach me.
thanks :D

---

### Post by steve.horsley on 2006-03-20
I just did a search on my system, and there are **loads** of .deb files in /var/cache/apt/archives. I suspect the entire installed system is there, but it may just be everything I have ever downloaded and installed (including every update). So that's where you can get the package fies from. 

I'm not sure of the best way to install them on the other system though. something like **dpkg --install whetever.deb** will probably do it, but there may be better ways. Maybe you could add a new repository pointing to the directory where you put these files.

---

### Post by Zimmer on 2006-03-20
[https://wiki.ubuntu.com/AptMoveHowto](https://wiki.ubuntu.com/AptMoveHowto)
you may find the answer here...

---

### Post by az on 2006-03-20
Here is a simple version of that howto if you don't need to redistribute that cd and bugger around with keys and stuff:
[https://wiki.ubuntu.com/AptMoveHowto/simple](https://wiki.ubuntu.com/AptMoveHowto/simple)

---

### Post by axl000 on 2006-03-20
thanks for the replys, but i still dont get it :S, i need to copy the packages to a usb drive, an then install the package form that, is it possible??

---

### Post by az on 2006-03-20
[QUOTE=axl000]thanks for the replys, but i still dont get it :S, i need to copy the packages to a usb drive, an then install the package form that, is it possible??[/QUOTE]
xubuntu-desktop is one package that has quite a number of other dependant packages.  If you install a fresh Ubuntu and then install ubuntu desktop, it will download a bunch of other packages with it.  You need to make all of those.

You could download them all to one directory and then run

sudo dpkg -i *

but that is unelegant and may cause you problems if you have more than just the xubuntu packages there.

---

### Post by dvarsam on 2006-03-20
I have created a Tutoria on this.

Read Article#:134921

Tutorial &#8211; How to get those valuable ".deb" Program Files & Back them Up

Hope it helps...

---


---
title: "Windows Emulation?"
date: 2008-03-25
forum: Absolute Beginner Talk
---

### Post by oblivioncth on 2008-03-25
I am not sure if this is emulation but I have seen it done before. What kind of program can I use to run windows (like 98 or XP) on Ubuntu. I have windows 98 and XP but I really just want to test things and such so I don't what to actually install for real, just to emulate then or what ever you call it.

---

### Post by LaRoza on 2008-03-25
For running Windows, use VirtualBox [http://www.virtualbox.org/](http://www.virtualbox.org/), or another VM. (VirtualBox is the easiest to use)

For running Windows programs, use Wine (see the wine subforum for more)

---

### Post by milton1 on 2008-03-25
you can run wine which will allow you to run windows programs, or you can install windows on a virtual machine, but you can not run windows on ubuntu; they are distinct operating systems. probably what you want is wine.
```
sudo apt-get install wine 
```

---

### Post by stoneybroke on 2008-03-25
Hi, If you want to run windows programs under Ubuntu then you need a program called Wine it is a windows emulator and you can get it here [www.winehq.org](www.winehq.org) if that is what you mean.

---

### Post by om1 on 2008-03-25
if you want something like emulation try wine [http://winehq.org](http://winehq.org) or you can just install it by running ```
sudo apt-get install wine
``` in your terminal
wine will let you run windows apps in linux

but if you want to create a virtual machine you can use the application in the previous post
a virtual machine lets you install and run a different OS inside of your own

---

### Post by om1 on 2008-03-25
> **stoneybroke said:**
> Hi, If you want to run windows programs under Ubuntu then you need a program called Wine it is a windows emulator and you can get it here [www.winehq.org](www.winehq.org) if that is what you mean.

you beat me to it :P i type to slow i guess

---

### Post by codeslicer on 2008-03-25
It is possible to use the VmWare Server with an existing Windows installation, more info here: [http://ubuntuforums.org/showthread.php?t=183209]("http://ubuntuforums.org/showthread.php?t=183209")

---

### Post by LaRoza on 2008-03-25
> **stoneybroke said:**
> Hi, If you want to run windows programs under Ubuntu then you need a program called Wine it is a windows emulator and you can get it here [www.winehq.org](www.winehq.org) if that is what you mean.

Wine Is Not an Emulator.

---

### Post by bubba_169 on 2008-03-25
The are quite a few programs available ... I like virtualbox but others like qemu (or kqemu which I think is faster)

To install virtualbox open a terminal and type

```
sudo apt-get install virtualbox-ose virtualbox-ose-modules-generic
```

then enter your password and agree to the installation. Afterwards you will need to start the vboxdrv driver by typing:

```
sudo modprobe vboxdrv
```

The last step is to add yourself to the vboxusers group. Go to System->Administration->Users and Groups, click the manage groups button, find vboxusers in the list it should be at the bottom and double click it, tick the box next to your name. Log out and back in again and you should be good to go... :)

---


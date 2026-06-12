---
title: "How do i run installed programs on linux debian and how to install a gui without inte"
date: 2013-04-02
forum: Any Other OS
---

### Post by johnsonparkar224 on 2013-04-02
Am new to linux and i dont have any gui installed. I would like 2 know which website 2 go 2, 2 download the gui and how do i install it after downloading. And how do i run installed programs such as python?

---

### Post by ManamiVixen on 2013-04-02
What do you mean "no gui"? What debian version are you running? What parts make up your computer such as cpu, ram, graphics, etc...

---

### Post by buzzingrobot on 2013-04-02
Your best bet is to go to [www.debian.org](www.debian.org) and peruse the documentation there.  

The primary Debian installer currently installs a GUI, Gnome. If you've installed Debian with no GUI, perhaps you used one of their more minimal installers.

Programs, like python, are typically run by simply entering the program's name and pressing the Enter/Return key. Note, though, that python is a programming language and the program called "python" interprets scripts written in the language.

---

### Post by UltimateCat on 2013-04-03
>  how do i install it after downloading. 

There are a few ways that you can install Debian after you download the OS.
You can take the downloaded ISO file and burn it to a DVD/CD or put it on a USB memory stick.

Once burned just put the DVD/CD in your drive and the installer will start the process of asking you questions and prepare your computer
for the complete install.
[http://www.debian.org/CD/live/](http://www.debian.org/CD/live/)


You should be able to open Synaptic Package Manager and use the search and type in 'python'
Synaptic will check the box next to the application. Right click on the package and "mark for installation" and click apply--

If you don't have Synaptic Package Manager installed that you will have to go to the Debian Repository and download it manually and use
the terminal to install it-

The current stable version of Debian is 6.0.7
[http://wiki.debian.org/DebianReleases](http://wiki.debian.org/DebianReleases)

Reading the documentation is highly recommended.

Unless; your building your OS manually-- I don't get why you don't have your GUI:~$ ?
Did you only install the bare minimal pkgs ?

---

### Post by UltimateCat on 2013-04-03
Make sure that you choose and download the correct ISO Image for your systems architecture.

For example I have a AMD Phenom Quad Core that is 64bit.
So when I downloaded Debian I made sure that I had the correct file.

> debian-squeeze_x86_64bit-iso-image (or something similar to that)


---


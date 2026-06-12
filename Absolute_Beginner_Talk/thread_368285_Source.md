---
title: "Source"
date: 2007-02-23
forum: Absolute Beginner Talk
---

### Post by claws_crystal on 2007-02-23
Hi everyone
                Im new to linux. I don't know what kernel is. I came to know that linux is free os and i can change its source. I know programming. How can I change source???

---

### Post by nickoli_02 on 2007-02-23
If you're new to Linux you probably don't want to change much of the source code and compile your own, though that is completely up to you. You can grab the source code of any version of the kernel over at [http://www.kernel.org/]("http://www.kernel.org/")

---

### Post by claws_crystal on 2007-02-23
How it will be ?? A text or any other form??
Do i have to install it for changing?? How can i know it is the same as that of Ubuntu

---

### Post by Tomosaur on 2007-02-23
Linux is just a kernel (the underlying operating system). Ubuntu is a **distribution** of Linux, which includes software and a desktop environment. All Linux distributions use a version of the kernel from [http://ww.kernel.org](http://ww.kernel.org). You need a Linux system to compile the linux kernel. MingW is a cross-platform project which some people have had success compiling the kernel on, but it's better to just pick a linux distribution. Compiling your own custom kernel can be a lot of work if you're brand new.

Most of the kernel is written in c, and as such, the source files are text files.

---

### Post by claws_crystal on 2007-02-23
then Can't i change my desktop environment??

---

### Post by Luk0r on 2007-02-23
You don't need to recompile the kernel to change your desktop environment.  Just install the one you want, i.e. if it's KDE, Gnome or Xfce, do *sudo apt-get install ubuntu-desktop* (Gnome), *sudo apt-get install kubuntu-desktop* (KDE) or *sudo apt-get install xubuntu-desktop* (Xfce).  The desktop environment will be available on the login screen dropdown menu.

---

### Post by Tomosaur on 2007-02-23
> **claws_crystal said:**
> then Can't i change my desktop environment??

Yes, you can, so long as you have the relevant software to download and install software, and a lot of patience. That is why it's not really a good idea to compile your own distribution yourself if you've never used linux before. Just pick a distribution, and install that. Most distributions are based on Debian or Red Hat - and these feature package management software which makes installing new software easier. I recommend a debian-based distribution (Ubuntu is debian-based).

---

### Post by claws_crystal on 2007-02-23
> **Luk0r said:**
> You don't need to recompile the kernel to change your desktop environment.  Just install the one you want, i.e. if it's KDE, Gnome or Xfce, do *sudo apt-get install ubuntu-desktop* (Gnome), *sudo apt-get install kubuntu-desktop* (KDE) or *sudo apt-get install xubuntu-desktop* (Xfce).  The desktop environment will be available on the login screen dropdown menu.
can it be readily available on ubuntu sys or we hav to download frm net???

---

### Post by Luk0r on 2007-02-23
Since desktops environments are usually large, they're probably not already on your CD, but those commands will download them from the 'net.  It might work if you had a kubuntu CD if you wanted to install kubuntu, but I'm not sure.

---


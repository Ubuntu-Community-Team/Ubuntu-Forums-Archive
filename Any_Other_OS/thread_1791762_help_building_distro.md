---
title: "help building distro"
date: 2011-06-27
forum: Any Other OS
---

### Post by FluxboxUser11 on 2011-06-27
I want to build my own distro based off of Ubuntu. How do I do this:

> The LFS system will be built by using an already installed Linux distribution (such as Debian, Mandriva, Red Hat, or
SUSE). This existing Linux system (the host) will be used as a starting point to provide necessary programs, including
a compiler, linker, and shell, to build the new system. Select the “development” option during the distribution
installation to be able to access these tools.

---

### Post by boydrice on 2011-06-27
It is not clear from your message what you need help with, or what you want a response to.  If you are trying LFS then good luck, just read carefully.

---

### Post by FluxboxUser11 on 2011-06-27
but where do I select "development" in the installation

---

### Post by jeffathehutt on 2011-06-27
```
sudo apt-get install build-essential
```

That will install the compilers and development tools on Ubuntu.  However, I am somewhat confused.  Are you trying to build a distribution based on Ubuntu, or based on LFS?  Linux from scratch has nothing to do with Ubuntu, though you can use Ubuntu or any other distribution to build LFS.  The procedure to make an Ubuntu derivative is very different than compiling LFS.

---

### Post by FluxboxUser11 on 2011-06-28
I am saying how do I make an LFS system based off of Ubuntu?

---

### Post by sanderd17 on 2011-06-28
This is not possible, you start from scratch (=from nothing) or from Ubuntu.

---

### Post by FluxboxUser11 on 2011-06-28
but it says you need another distro to make it

---

### Post by sanderd17 on 2011-06-28
Ah, that is like you need a computer to type a text document.

It's not based on Ubuntu, but you use the tools in Ubuntu to create it. In that case you need to install the build-essentials.

---

### Post by FormatSeize on 2011-06-28
> **FluxboxUser11 said:**
> I am saying how do I make an LFS system based off of Ubuntu?
I've been doing LFS for a few days now (like someone said earlier, read carefully or you will spend a lot of time starting over). 
 
To make a LFS that is based on Ubuntu, you have to first build LFS (that, as I am finding, is the hard part). Then from there, grab the BLFS (Beyond Linux from Scratch) book, which will tell you how to go about installing things on top of your system. The book will tell you how to go about installing X and Gnome. Then, you will have a basic Gnome environment, then you can add various components along the lines of what you see in Ubuntu from the repositories. 
 
Now, either this is not easy, or I am going about doing it the hard way (or both). But, at least from how I am experiencing it, it takes a lot of work to put a Linux system together from scratch. And then, the desktop environment is even harder since you have to get a whole bunch of stuff, their dependencies, and their dependencies' dependencies. Currently, I am working on getting X installed. Next, I plan trying to get a simple desktop environment working. This could be easier, but I don't have aptitude or anything like it on this system I'm building, so the internet isn't an option yet for downloading and installing. I have to compile them all, and I'm not quite good enough with scripting to have everything in a directory recursively compiled (is that possible?). 
 
Anyhow, good luck.
 
> **FluxboxUser11 said:**
> but it says you need another distro to make it
You do. You need a computer to build the system is basically what they are saying. The system on which you build LFS is called the host system, which has what you need to build your new system (mouse, monitor, keyboard, commands, a text editor). I'm using Slackware as my host, and I plan on building a Gnome-like desktop environment when all is said and done. Your new system will actually be on another partition which you will set up as a target for all the commands that you input as you build it. You will be building tools and basic things that you will need to have a system that will work well enough to have you log in and compile other things.

---

### Post by ventrical on 2011-06-28
An example of creating an OS while using another distro is that of Winddows XP. It was developed from scratch , with the MS-DOS 5.0 operating system running a compiler called QuickBasic.

With Linux is is much easier. There are demos and tutrorials of how to make remiz distros of Ubuntu or you can make you own bonifide Ubuntu version.. but I think you are trying to say that you want to build an OS while running the Ubuntu operating system as your platform??

If I have time I will try to trackdown some links (if someone else hasn't already.

---

### Post by ventrical on 2011-06-28
> **FluxboxUser11 said:**
> I want to build my own distro based off of Ubuntu. How do I do this:


If you download he latest Debian distro, burn it to a DVD and then install it it will come up with a "development' option box to be ticked off.

---


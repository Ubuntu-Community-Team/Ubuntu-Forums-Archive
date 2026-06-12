---
title: "To install Arch, do I need intimate knowledge of my hardware?"
date: 2008-02-23
forum: Arch and derivatives
---

### Post by Pogeymanz on 2008-02-23
For example, do I need to know exactly what graphics card I have and what kind of screen is on my laptop, etc?

The only thing I know about my laptop's hardware is that it has an evil broadcom wireless card.

Some people have hinted that the installation of Arch is very difficult, but some say it isn't that bad. I'm not afraid of text, so long as it's clear as to what I'm being asked to do.

---

### Post by fwojciec on 2008-02-23
Most of the hardware is going to be configured automatically by the kernel -- you do need to know your graphics card, wifi card and any problematic pieces of hardware.  In case you run into problems you can always get a list of your hardware using the "lspci -v" command, and then it's just a matter of googling things to see how something can be made to work in Linux.  

With Arch you are not being asked to do anything -- it is you who is asking computer to do things.  Of course, that produces a problem because you need to know what to ask of your computer, especially at first -- this is where the [Beginners Guide](http://wiki.archlinux.org/index.php/Beginners_Guide) comes in.  It's definitely a good idea to use it when you're installing Arch for the first time -- I still use it if I have to reinstall as a kind of checklist to make it easier for myself to remember all the things that need to be configured along the way.

---

### Post by Rumor on 2008-02-23
I've installed Arch on a number of computers and with only one exception, the kernel install has automatically detected and set up my hardware fine. 
For setting up X where I do not know the graphics chipset, I have done as fwo suggests and searched the return of lspci to see what chipset is detected and then searching with pacman for the drivers for that set, OR I've used hwd (info here: [http://user-contributions.org/projects/hwd/hwd.html](http://user-contributions.org/projects/hwd/hwd.html)). In *most* cases running hwd -xa has given me a working xorg.conf file

---

### Post by Crooksey on 2008-02-23
Its not essential, but like anything, the more you know and "trim" your dsitro, the more it will work for you.

---

### Post by ynnhoj on 2008-02-24
> **EmosSuck777 said:**
> Some people have hinted that the installation of Arch is very difficult, but some say it isn't that bad. I'm not afraid of text, so long as it's clear as to what I'm being asked to do.
i don't think installing arch is at all difficult.  since you're not afraid of text, read this: [arch's installation guide](http://archlinux.org/static/docs/arch-install-guide.txt).  there aren't many things that the installer requires you to do, really --- the one thing i might have found a bit daunting the first time i installed arch was having to edit some of the configuration files (not something i was used to as an ubuntu user :o), but the install guide and wiki covered all of that stuff, so all was well.  as it turned out, there wasn't even much that i needed to add or change, 'cause my setup is simple.

---

### Post by K.Mandla on 2008-02-24
> **EmosSuck777 said:**
> For example, do I need to know exactly what graphics card I have and what kind of screen is on my laptop, etc? ...
Knowledge yes, intimate knowledge ... no, but it doesn't hurt either.

I usually install Ubuntu on a mystery machine first, make a note of the hardware, modules, drivers and so forth, and then try it with Arch. It's just the way I learned to do business. :roll:

---

### Post by mivo on 2008-02-24
Provided you know what video card or chipset you have, the excellent and already mentioned [Beginner's Guide]("http://wiki.archlinux.org/index.php/Beginners_Guide") will get you through. If you use a laptop, you'll also want to know what wireless chipset/card you have. Nothing else is really needed to get up and running. :).

---

### Post by bwtranch on 2008-02-25
> **fwojciec said:**
> Most of the hardware is going to be configured automatically by the kernel -- you do need to know your graphics card, wifi card and any problematic pieces of hardware.  In case you run into problems you can always get a list of your hardware using the "lspci -v" command, and then it's just a matter of googling things to see how something can be made to work in Linux.  

With Arch you are not being asked to do anything -- it is you who is asking computer to do things.  Of course, that produces a problem because you need to know what to ask of your computer, especially at first -- this is where the [Beginners Guide](http://wiki.archlinux.org/index.php/Beginners_Guide) comes in.  It's definitely a good idea to use it when you're installing Arch for the first time -- I still use it if I have to reinstall as a kind of checklist to make it easier for myself to remember all the things that need to be configured along the way.
Pretty much everything is covered in the Beginners Guide. You might want to print out the salient part before you start. A good thing to do, if you have a problem is look at your ```
 nano /etc/dc.conf
``` and see if you have your eth set right. If you get the net back, piece o' cake. Course you might have other issues, say if you have wireless or on a LAN, whatever. But, it's really easy.

---

### Post by Crooksey on 2008-02-25
> **bwtranch said:**
> ```
 nano /etc/dc.conf
``` and see if you have your eth set right. 

```

/etc/**rc**.conf
```

---


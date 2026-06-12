---
title: "Ubuntu and the command line"
date: 2008-02-13
forum: Absolute Beginner Talk
---

### Post by dman777 on 2008-02-13
Hello, 

I am currently using Gentoo because I like to do everything from the command line and I do not use desktop software. But there isn't much support in Gentoo any more and so I am thinking about switching Linux's. I have some questions:

1) Is there a list of console programs for Ubuntu that I can look at? I couldn't find a list on the Ubuntu wiki.

2) Are there documents showing what files to edit for drivers, explaining system files(like editing drivers), ect?

3) Is XGL still obtainable for Ubuntu?

---

### Post by hyper_ch on 2008-02-13
(1) I guess the console programs for Ubuntu are the same as for Gentoo - but you don't ahve to compile them all yourself...

(2) config files should also be the same as for Gentoo...

(3) Not sure what you mean by this.

---

### Post by dman777 on 2008-02-13
(3) I can't find a way to get XGL through the portage tree and there is no overlay that I can find for it. XGL is a graphics accelerator that is not really being developed anymore. But the fglrx ATI driver isn't compatible with AIXGL so I need XGL. I was wondering if it is still obtainable with Ubuntu.

---

### Post by jan quark on 2008-02-13
perhaps you mean

xserver-xgl

this is still active and works with ati cards

---

### Post by Crooksey on 2008-02-13
A list of console programs?

Ubuntu's repo's mixed with all 3rd party repo's will have the same programs as gentoo, you wont have to use any diffrent programs, just install them on ubuntu.

Also XGL is an xserver, so using the ubutu xserver-xgl will be the same as gentoo, before switching though I would look at other distro's, try either something like Debian or Arch.

---

### Post by dman777 on 2008-02-14
ya, i thought about using debian also. i'm sure this has been asked a million times so please forgive me...if a software runs on debian then it sould run on ubuntu and vice versa, right? One of the things that draws me to Ubuntu is all the software for it.

---

### Post by hyper_ch on 2008-02-14
> **dman777 said:**
> ya, i thought about using debian also. i'm sure this has been asked a million times so please forgive me...if a software runs on debian then it sould run on ubuntu and vice versa, right? One of the things that draws me to Ubuntu is all the software for it.

Mostly yes - but not always.

However, you can always compile from source ;)

---

### Post by kesman on 2008-02-14
And by the way, the newest fglrx DOES support AIGLX, check [http://wiki.cchtml.com/index.php/Main_Page](http://wiki.cchtml.com/index.php/Main_Page)

---


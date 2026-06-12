---
title: "What is gcc make and perl?"
date: 2007-03-20
forum: Absolute Beginner Talk
---

### Post by linuxjerk on 2007-03-20
What is gcc? Is this a C compiler? Is this program already installed on my ubuntu 6.10?
Or do I have to install it?
What is MAKE?????
What is PERL???
Are these on my install of 6.10? Do I have to install them or make them active?
Clueless

---

### Post by mac.ryan on 2007-03-20
> **linuxjerk said:**
> What is gcc? Is this a C compiler? Is this program already installed on my ubuntu 6.10?  Or do I have to install it? 

Yes, GCC = GNU C Compiler. I don't remember if it is automatically installed at the beginning. If not, you can install it from System --> Administration --> Synaptics Package Manager.  (See below for more details) 

> What is MAKE?????

"make" and "make install" are two commands you have to use when compiling software on your own. Simplifying, "make" compiles the source code, while "make install" makes your newly compiled software part of your system.

> What is PERL???

it is a programming language. ([http://en.wikipedia.org/wiki/Perl](http://en.wikipedia.org/wiki/Perl))

> Are these on my install of 6.10? Do I have to install them or make them active?

If they are not already installed, you can do via Synaptic (see above). In ubuntu, almost all of the software you will ever need, is stored in one of the  central locations called "repositories". Synaptic is the "mediator" between such repositories and your system: i.e. whenever you want to install a new software (or repair a broken installation, or uninstall something) you do it via Synaptic.

Now, for GCC or PERL, you can simply:
[LIST=1]
[*]launch synaptic
[*]search for the software you need (e.g.: type "gcc" in the search box)
[*]thick the box beside the name ("mark for installation" option)
[*]click apply[/LIST]...and the trick is done!! ;)

Should you urgently need more definitions, you can easily look them up on google  using the "define" function (e.g.: type "define:perl" or "define:gcc" in the search box).

Anyhow... people on the forum is always here to help... :)

---

### Post by linuxjerk on 2007-03-21
Wow I was completly unaware of the selection of sofware available on ubuntu.
Thanks for the info

---


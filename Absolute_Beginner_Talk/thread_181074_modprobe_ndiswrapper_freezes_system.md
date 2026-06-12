---
title: "modprobe ndiswrapper freezes system"
date: 2006-05-23
forum: Absolute Beginner Talk
---

### Post by thefamousnomo on 2006-05-23
hello people

been having massive issues trying to get wireless up and running :-k 

have read loads of posts in here and googled a lot but cant get past two hurdles;

1. sudo modprobe ndiswrapper freezes my system

2. cant seem to compile any binaries! ie. installed build-essential and kernel headers but cannot 'make' anything. im sure that i have set up the virtual link ok... (this is referencing ndiswrapper too, trying to install 1.16 to see if this doesnt freeze machine)

according to *[http://www.smallwhitecube.com/php/dokuwiki/doku.php?id=howto:tew424ubv2](http://www.smallwhitecube.com/php/dokuwiki/doku.php?id=howto:tew424ubv2) *it should work (same chipset as the dongle im trying to use...)

thanx

---

### Post by skinnygmg on 2006-05-23
see if this helps...

[http://www.fedoraforum.org/forum/showthread.php?t=20472](http://www.fedoraforum.org/forum/showthread.php?t=20472)

---

### Post by thefamousnomo on 2006-05-23
[QUOTE=skinnygmg]see if this helps...

[http://www.fedoraforum.org/forum/showthread.php?t=20472](http://www.fedoraforum.org/forum/showthread.php?t=20472)[/QUOTE]

interesting reading my friend! but basically is seems that the version of ndiswrapper is at fault! but, without being able to tackle point 2, i cant try any other versions...

any takers for point 2

any chance for me lads? (name the film!)

cheers

---

### Post by az on 2006-05-23
[QUOTE=thefamousnomo]hello people

been having massive issues trying to get wireless up and running :-k 

have read loads of posts in here and googled a lot but cant get past two hurdles;

1. sudo modprobe ndiswrapper freezes my system[/QUOTE]


What chipset?  This is probably due to the fact that the ubuntu kernel has a lot of wireless cards already supported.  When two drivers compete for the same hardware, this can happen.  You should either try to get the native linux driver to work, or blacklist it so that ndiswrapper can work.

You may also have an inf file that is too old.  Most windows drivers that are shipped with the card are already too old for ndiswrapper.

Look at the ndiswrapper changelog and see if support for your card has been added since the version in Ubuntu.  In 99 percent of all cases, the one in Ubuntu should work fine.  You almost never have to recompile ndiswrapper.

To copmile something, you need to install build-essential (which is on your cd).  Additionaly, since the kernel was not made with the same compiler version, to compile a kernel module, you need the linux-headers package as well as gcc-3.4.  The headers are on the cd, but only gcc-4.0 is on the cd....



There is a binary driver howto on the wiki.

---


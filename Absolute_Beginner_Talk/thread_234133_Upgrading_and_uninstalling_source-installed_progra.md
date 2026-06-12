---
title: "Upgrading and uninstalling source-installed programs (ie. not apt-get)"
date: 2006-08-11
forum: Absolute Beginner Talk
---

### Post by anroy on 2006-08-11
On one hand I am a newbie at Linux, I come from the wonderful world of Windoze. :-$ 

On the other hand I am a developer so I have to do all kinds of non-newbie stuff.  A conundrum, tis.

Because I have to set various config options I have only ever installed MySQL, Apache and PHP by downloading the source tarballs and doing the usual "configure / make / make install" sequence.

My two questions:

1) How do I upgrade these programs.  eg.  from PHP-5.0.2 to PHP-5.0.14, etc.?
Can I just do the exact same thing, install into the exact same target directory?  If you don't know the specifics of MySQL, Apache or PHP that is OK, but in Linux generally does this kind of thing work?  Or is there some hidden "Registry" type of concept as there is in Windows?

2) How do you generally uninstall programs that you have installed from source tarballs?  Again, even if you don't know the answer for MySQL, Apache or PHP that is fine, I am just trying to get an idea of what is normal in Linux.  

I realize that on this forum the majority of people use apt-get for these tasks but there must be at least some of you installing from source.

Thanks!

---

### Post by Perfect Storm on 2006-08-11
1. It really depends on how the application/libs/program are made but mostly you can do that. 

> Or is there some hidden "Registry" type of concept as there is in Windows?

Thank god, no.
But some compile application you can use checkinstall instead of make install so it show up in synaptic package manager which make it easy to uninstall if you don't want to unpack the source.

2. Many of the source have a script to uninstall option. If you unpack the source:
```
cd the unpacked source
sudo make uninstall
``` should do it.

---


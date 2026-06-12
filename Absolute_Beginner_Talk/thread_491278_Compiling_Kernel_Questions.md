---
title: "Compiling Kernel Questions"
date: 2007-07-03
forum: Absolute Beginner Talk
---

### Post by grim1234 on 2007-07-03
HI, If I'm compiling a kernel for use with a 7.04 i386 install, does it matter which version of the kernel I compile?

Are there likely to be any compatibility problems with 2.6.21 instead of 2.6.20-15?

Do the modules need to be a specific compiled separately? 

Any links for background reading would be appreciated (I've read the ubuntu doc pages). Thanks!

---

### Post by moore.bryan on 2007-07-03
*i put [this]("http://ubuntuforums.org/showthread.php?t=266666") together quite a while ago and i don't know if it'll give you any more insight than what you've already read... any reason why you want to compile a new kernel?*

---

### Post by annda on 2007-07-03
you can read that too:
[http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158)

also, i highly recommend the [gentoo dox]("http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=1&chap=7#doc_chap3") to get the idea of what kernel compilation is like - just as an illustration.

---

### Post by 7H4_D00D3 on 2007-09-03
Hi!

First post at ubuntu forums ever :D

This site has proven very useful for me so I finally decided to register :D

I recently compiled kernel 2.6.22.6 but I have a couple of questions about it

a) The resulting debs are TOO big, one is 8Mb and the other 84 Mb, but the packages from ubuntu are not bigger than 55Mb or so. How come those files are bigger than ubuntu's default if I chose not to compile A LOT of modules

b) There are some stuff listed on that kernel that I didnt want to be there, for instance, when I xconfiged it I removed support for minix fs and stuff like that, but when I checked on the details of the debs, under fs there was listed minix

Right now I'm using feisty with kernel 2.6.20.15-generic, what I did was I downloaded the 2.6.22.6 kernel from kernel.org and un-tared it on /usr/src, I copied there the .config file for the 2.6.20.15 kernel and then on a terminal I used make xconfig to edit that .config file so I could customize my kernel, when I was done I saved the changes and proceeded to make the kernel packages and finally noticed what I posted above

thanks for the help! :)

---


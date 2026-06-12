---
title: "after boot i get a black screen"
date: 2005-09-26
forum: Absolute Beginner Talk
---

### Post by marvermaas on 2005-09-26
hello people,
 I have the following problem: I just installed Ubuntu on a computer for the first time (first time I did any thing with linux), and after installation I am asked to remove the cd and let it restart. Fine that done, now I only get a black screen after the initial boot.

Help!!! 

I ran the memtest option (seemed to work) in the boot menu and also the other option but I don't know wat to do with the command promt when I get there. 

I hope someone can give me a hint

MarV

---

### Post by mlomker on 2005-09-26
> I ran the memtest option (seemed to work) in the boot menu and also the other option but I don't know wat to do with the command promt when I get there. 


Log in using the 'recovery mode' option and from a prompt run **dpkg-reconfigure xserver-xorg**.  Change your video card driver to something different and take the defaults for anything that you're not sure about.  If you're not sure about which video selection to try, then 'vesa' is the slowest but most compatible.

---

### Post by marvermaas on 2005-09-26
Thanks a lot, I haven't got it working just yet but now Iknow where tot start

MarV

---


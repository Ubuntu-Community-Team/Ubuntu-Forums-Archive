---
title: "easiest way to reeconfigure xserver.xorg"
date: 2008-01-29
forum: Absolute Beginner Talk
---

### Post by sports fan Matt on 2008-01-29
im having alot of trouble trying to reconfigure xserver.xorg..

I can hit enter, all the way to past where it lists my driver to reconfigure then i attempt enter or space bar and nothing occurs..What am i doing wrong?  is the command still sudo apt-get reconfigure xserver.xorg?  

Thank you all for helping a person who feels like a fool..(me) :)

---

### Post by aeiah on 2008-01-29
sudo dpkg-reconfigure xserver-xorg is what you're after i think, although this may not solve your problem, depending on what your problem is

---

### Post by sports fan Matt on 2008-01-29
My issue is i accidently loaded some of the x window envoroment i think, and everytime i run synmaptic i get a black background then the regular screens..doesnt matter what i run either..id hate to reinstall for such a small issue..

I have some things like things from the xbase clients which i dont want..I dont know how i can get rid of them either..anyone have any ideas on what in the z base clients i can safely remove so my mouse isnt that jumpy?

Also, what can i do in recovery mode to fix the drivers problem (I think i accidently installed a driver i didnt want ..I have a intel celeron cgc chipset graphics controler and id love to use it if possible...any ideas?

---

### Post by stump138 on 2008-01-29
try doing it in this fashion
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
and see how that works for you.

---

### Post by steveneddy on 2008-01-29
> **stump138 said:**
> try doing it in this fashion
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
and see how that works for you.

I was just about to say that.

---


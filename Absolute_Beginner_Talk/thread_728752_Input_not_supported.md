---
title: "Input not supported"
date: 2008-03-19
forum: Absolute Beginner Talk
---

### Post by taash on 2008-03-19
Hi I'm totally new at Linux & Ubuntu and I'm really stuck
 I have Dual Boot XP with Ubuntu 7.10 and I had problems with my graphics card on installation. Since nothing that i had tried appeared to work I fixed  it by downloading the Alpha version of  Heron and then when i tried tried to install the again it worked fine using the forums help. The problem i have now is that everytime that i try to put a game I get "Input Not Supported" I have an Acer AL1916w with an ATi1650x 512 card. When i connected the pc to another monitor it works fine. how can i fix this please.

---

### Post by oskar2000 on 2008-03-19
Well... seems to be a hardware problem, and I can't do more than google for it either... unlikely that someone who has had the same hardware will come along.

[http://www.jimbo7.com/wiki/index.php?title=AL1916W_LINUX_WIKI](http://www.jimbo7.com/wiki/index.php?title=AL1916W_LINUX_WIKI)

Take a look if the "monitor" section in your xorg.conf is set correctls... the rest doesn't seem to apply to you. Don't forget to make a backup before you edit it!

---

### Post by linuxtoindia on 2008-03-19
''sudo dpkg-reconfigure xserver-xorg'' try this 
then reinstll gdm

---

### Post by taash on 2008-03-21
Thanks it worked!!!!!!!!!!

---


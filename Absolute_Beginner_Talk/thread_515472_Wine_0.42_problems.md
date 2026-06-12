---
title: "Wine 0.42 problems"
date: 2007-08-02
forum: Absolute Beginner Talk
---

### Post by SnoopDeVille on 2007-08-02
Hello folks, im on amd64 Feisty Fawn, 

my problem is that with each release of a new wine it seems like a massive downgrade,

each time i tried installing newer versions something started going wrong. 

With wine 0.40 i had sound problems..... with 0.41 my alt-tabbing made me crash here and there

and in 0.42 i'm getting the same thing, but on a much larger scale .


The problem is also, that i installed Gdesklets from a .deb file compiled for 64bit and while they 

worked it messed up my system, so that it doesn't know how to open application files (i.e. even 

debs) so i have to do everything manually. So my question is, how do i run a .deb package 

from the terminal ? (yes im a noob) 

thx :>

p.s. ( i reeeeaalllly need to reroll on wine 0.39)


EDIT: problem Solved , seems i had a huge-load of libraries and dependancies altered , managed to fix em up , wine suddenly started working as intended ! :) 

YATA ! :)


EDIT2: seems when i closed the special effects (4 desktops and beryl/compiz) it magicaly started working properly :P

---

### Post by avik on 2007-08-02
> So my question is, how do i run a .deb package

from the terminal ?

Glad you got it fixed.  Just in case you still want to know:

[CODE]sudo dpkg -i *<name_of.deb>*

---


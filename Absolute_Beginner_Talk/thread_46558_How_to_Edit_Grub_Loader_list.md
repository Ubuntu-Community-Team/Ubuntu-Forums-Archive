---
title: "How to Edit Grub Loader list?"
date: 2005-07-05
forum: Absolute Beginner Talk
---

### Post by Bl0wn2b1ts on 2005-07-05
Howdy!

I have just installed ubuntu as a dual boot with my XP 

can anybody please explain how to change grub so it uses xp as the default os and you have to choose ubuntu???

sorry guys/gals I know this is a linux forum! its just my missus will give me earache if it doesnt just go straight to what she knows! and I am up for trying ubuntu!

i have had a good look around but still can not figure it out  ](*,) 

thanks in advance  :-P 

Bl0wnb2b1ts

---

### Post by mailcameel on 2005-07-05
edit as root:

/boot/grub/menu.lst
( vi /boot/grub/menu.lst )

add:

default 0

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.

So default is set to 0. ( The first entry )

---

### Post by Bl0wn2b1ts on 2005-07-05
thanks a lot!

just found it in the unnoficial ubuntu starters guide!

right im off to try it will let you know how it goes!

cheers

Bl0wn2b1ts

---

### Post by Bl0wn2b1ts on 2005-07-05
working a treat thanks!

Bl0wn2b1ts

---


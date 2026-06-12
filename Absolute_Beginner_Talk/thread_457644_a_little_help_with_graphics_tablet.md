---
title: "a little help with graphics tablet?"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by Gmbrdilos on 2007-05-28
I have an Acecad Flair II graphics tablet
it seems to work plug and play right away, however it is way off from where it is supposed to be.
Hard to explain but simply put, the mouse pointer is not always at the position it is supposed to be when I move the pen around.

EDIT: also pressure sensitivity does not work.

---

### Post by SoulinEther on 2007-05-28
Give me a minute, i'll try out my tablet, haven't tried it in any linux since edgy.

---

### Post by Gmbrdilos on 2007-05-28
you have an acecad flair also?

---

### Post by SoulinEther on 2007-05-28
No, but I have a tablet that wont work in Feisty.

Uh.. not to make this really ironic, but what did you do to get your tablet to "work"? Does it function as a mouse? Because mine is a nice paperweight.

---

### Post by Gmbrdilos on 2007-05-28
I did absolutely nothing It just worked when I pluged thats all, but I guess yea it works like a very bad mouse that is just comfortable to hold... and a paperweight...

---

### Post by SoulinEther on 2007-05-28
This might help with you... don't know.

[http://alexmac.cc/tablet-apps/](http://alexmac.cc/tablet-apps/)

I installed it and ran it, but all it sees is my mouse. It's supposed to provide configurations for all tablets, maybe it'll work for you. They have a .deb for ubuntu, too.

---

### Post by Gmbrdilos on 2007-05-28
as far as I can tell that is just for wacoms

---

### Post by Gmbrdilos on 2007-05-28
yep all it sees is my mouse

---

### Post by SoulinEther on 2007-05-28
Well we're both in some Tablet limbo i guess..

I'll keep looking.

---

### Post by Gmbrdilos on 2007-05-28
found this but confused me even more: [http://acecad.sourceforge.net/index.html](http://acecad.sourceforge.net/index.html)

---

### Post by SoulinEther on 2007-05-28
I suppose

modprobe acecd

gave a fatal result?

---

### Post by Gmbrdilos on 2007-05-28
not really sure what you mean

---

### Post by SoulinEther on 2007-05-28
Open up a terminal and type in **modprobe acecd**. According to that site that you linked... if its going to work without some serious tweaking that should not result in [B]FATAL: Module acecd not found.
[/B]

---

### Post by Gmbrdilos on 2007-05-28
oh, it did result in FATAL: Module acecd not found

---

### Post by SoulinEther on 2007-05-28
[http://acecad.sourceforge.net/README](http://acecad.sourceforge.net/README) has what you need but I don't know how exactly to do it myself either. :S

---

### Post by Gmbrdilos on 2007-05-28
that readme scares me

---

### Post by Gmbrdilos on 2007-05-29
anyone else has any ideas?

---

### Post by Gmbrdilos on 2007-06-05
*bump*

---

### Post by Nekiruhs on 2007-06-05
I don't know much about the tablet, but from the looks of the readme, you have to compile a driver for it. Not too hard in Ubuntu.

---

### Post by Gmbrdilos on 2007-06-05
I got lost along the way while reading the Read Me. Can some one break it down for me?

---

### Post by Glimps on 2007-06-14
Feisty comes with the acecad drivers. If you check your dmesg when you plug your table, you will see it does use the acecad drivers. Thing is I can't figure out how to enable it in Gimp, nor use pressure. 

If you open up Gimp and check the File>Preferences>Input devices and try to configure it, it doesn't get detected. 

The acecad project doesn't seem very active so I guess we'll need some Ubuntu wiz to help us out here.

---

### Post by Gmbrdilos on 2007-06-16
yes I know the acecad driver from the repos is installed. but the cordinates are off and pressure sensitiviy wont work. I think I have read that this will be fixed in gusty

---


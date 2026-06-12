---
title: "Burning Image Files .mdf"
date: 2006-09-17
forum: Absolute Beginner Talk
---

### Post by Dr Von Bon Bon on 2006-09-17
How would I go about doing this please?

What software do I need to burn image files on Ubunutu?

Thanks.

---

### Post by bulldog on 2006-09-17
Well I use K3b without a problem.

Have to say I don't do any sophisticated burning with it,but it's good enough for my needs.

---

### Post by vinay.v on 2007-03-06
I know I'm replying very late.. But it might be useful for people like me who are searcing for answer to this very question. How do I write a mdf/mds image to a CD?

k3b might be a really good burner. But it is not installed by default in Ubuntu (& maybe you need kubuntu or atleast kde libs for k3b to work. I'm not sure about that).

Instead, I installed a very small (7kb) program **"mdf2iso"** from apt-get. This allows you to create an iso file(or even cue/bin or toc image)  from mdf image. Once it is converted to iso, just right-click the file in Ubuntu & choose "Write to disc".. 
Simple, right? :)

---

### Post by Timokl on 2008-07-23
Hi vinay,

you can install any KDE application with Ubuntu's Gnome Desktop.

Just fire up a terminal and type:

sudo apt-get install k3b

And then brew a coffee, because apt-get will download a lot of kde-files that k3b needs to run - and that's about 100 MB or so.

After that, you find k3b in the applications menu just like any other program.

Timo

---


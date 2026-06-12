---
title: "command line problems with install etc"
date: 2006-10-10
forum: Absolute Beginner Talk
---

### Post by carloslosgrande on 2006-10-10
Hi there everyone. Got an annoying little problem. I'm trying to load a program for mp3 called Gogear. I've assiduously followed the instructions that came with it, and a few "how to's" I've been directed to in this forum but it just won't work!:evil: ](*,)
I finally got the file recognised but I can't 'make' it or anything else. I've attached a screenshot [may be a little blurry] that has the errors I get.
Is this just *me* doing it all wrong or is there something fundamental missing from my system?:confused:
This particular app was written specifically for my type of mp3 player to do exactly the things I want, in Linux, so I'm persevering but am ssooooooo frustrated.
I'm in the tunnel but where's the damn light gone?

---

### Post by halitech on 2006-10-10
never mind, I see you did extract the file, or at least the folder is showing up

can you post the contents of whats in the folder?

---

### Post by meng on 2006-10-10
List the contents of the directory please.
ls

---

### Post by halitech on 2006-10-10
did you follow these steps exactly?

QUICKSTART (openGogear installation)
	1) tar jxvf openGogear-0.01.tar.bz2
	2) cd openGogear-0.01
	3) make
	as root:
	4) make install
	5) just type gogear for usage infos

---

### Post by carloslosgrande on 2006-10-10
Hi Halitech, attached is a screenshot of the folder. and yes I followed those steps exactly, as far as 3, which didn't work. the command - make - needs some other operand, a 'make target'

---

### Post by halitech on 2006-10-10
you don't need to do a ./configure, just make and then sudo make install although I'm getting an error when I try to install it about SQLlite so not sure whats up with that

---

### Post by halitech on 2006-10-10
Just noticed you went with the java version where I went with the normal version (or something like that)

is there any reason why you didnt go with the deb installer?

[http://sarovar.org/download.php/524/opengogear_0.01-1_i386.deb]("http://sarovar.org/download.php/524/opengogear_0.01-1_i386.deb")

may need to install libid3-3.8.3 (least I did)

---

### Post by carloslosgrande on 2006-10-10
Hi Halitech, 1st, the SQLite is the thing needed by gogear to do the prepping for the music files to actually play. I have SQLite.
2nd, the idlib3-3.8.3 is out of date and my system uses idlib3-3.8.3c2a and when I tried to install idlib3-3.8.3 it warned me against it - I assume that other apps use this. I believe the java version has overcome this - but I don't know that for certain.
I only tried ./configure after the other didn't work. I followed the instructions that came with gogear initially.

---

### Post by carloslosgrande on 2006-10-10
Hi Meng, which directory? /tmp? its on the screenshot already posted.

---


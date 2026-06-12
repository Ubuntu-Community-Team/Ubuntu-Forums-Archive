---
title: "GDM could not write to authourization file"
date: 2007-06-04
forum: Absolute Beginner Talk
---

### Post by Redd2 on 2007-06-04
Hi all:

I'm total newbie to trying to fix my own computer problems, but I want to learn so I don't have to rely on others...so here I am looking for info...

I can't log in, the error message says "GDM could not write to authorization file", it continues to say that the hard disk space may be full...

I've read a couple posts that suggest to enter code to resolve this issue, can anyone tell me how to get to the screen to allow me to enter in the command line & what commands I need to use to be able to free some disk space, I know the files I need to remove, they'll be music files. Will it be evident once I'm in where to go to delete these or what?

Your help will be greatly appreciated...

redd2

---

### Post by jiminycricket on 2007-06-04
Hi, this could be one of two issues

First, [https://help.ubuntu.com/community/RootSudo#head-0c932eb3f1619126fc8307ee7690f462552d34ec](https://help.ubuntu.com/community/RootSudo#head-0c932eb3f1619126fc8307ee7690f462552d34ec) If you've ever run a graphical app with sudo, that could cause this problem.  You can use gksudo intstead.

The second one is to login to a text terminal.  Press CTRL + ALT + F1 to go to tty1.  Then login with your normal name.  

Type:

sudo aptitude clean && sudo aptitude autoclean

Also try removing the ICE file:

rm ~/.{ICE,X}authority

---


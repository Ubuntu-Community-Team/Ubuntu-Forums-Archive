---
title: "unrar problem:("
date: 2006-02-06
forum: Absolute Beginner Talk
---

### Post by cobweb on 2006-02-06
hi everyone, i'm new to linux, installed ubuntu just a couple of hours ago..
and so i need emergent help.. i wanna unrar my .rar files which i can reach from windows, but when i run " apt-get install rar " ir gives the error:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package rar
in fact this could not find package error is given when i try to download emacs..

how can i unrar my files?
thanx in advance..:cry:

---

### Post by kaamos on 2006-02-06
Hello!

You don't need to know the exact package names: [https://wiki.ubuntu.com/SynapticHowto](https://wiki.ubuntu.com/SynapticHowto)
search for "rar" in synaptic.
search for "emacs" in synaptic.

---

### Post by cobweb on 2006-02-06
well, the next problem is i cannot open it by System -> Administration -> Synaptic Package Manager, it simply does nothing when i click on :confused:

---

### Post by nik on 2006-02-06
you probably want unrar-nonfree

you need to enable universe and / or multiverse to get it...

---

### Post by nik on 2006-02-06
try 

sudo synaptic

in a terminal

---


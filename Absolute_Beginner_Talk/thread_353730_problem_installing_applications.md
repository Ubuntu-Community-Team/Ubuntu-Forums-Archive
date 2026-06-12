---
title: "problem installing applications"
date: 2007-02-05
forum: Absolute Beginner Talk
---

### Post by Guus on 2007-02-05
hey all,

Yesterday i wanted to install Blender (among other apps) on my new 6.06 system.

this PC is not conencted to any internet conenction so i decided to install it via the Ubuntu live cd.

Ubuntu offered to to open the CD via Synaptic package manager,  it didnt work.

so i decided to do it in the add/remove menu. i get the following message at each application:

[IMG]http://img204.imageshack.us/img204/4477/screenshotka0.png[/IMG]

can someoen offer some help?

Thx in advance :)

---

### Post by phossal on 2007-02-05
Will it let you get something like build-essential?

---

### Post by Guus on 2007-02-05
> **phossal said:**
> Will it let you get something like build-essential?

im not sure what you mean :(

can you explain?:)

---

### Post by phossal on 2007-02-05
If you're using the CD to try to install things, will the CD allow you to pull build-essential? build-essential is a package. Or how about ndiswrapper?

---

### Post by 3rdalbum on 2007-02-05
When you first install Ubuntu, it only knows about what is available on the Ubuntu CD. Blender isn't on the CD, so that's why the Add/Remove Applications program can't find it.

You really need an internet connection to install programs on Linux, otherwise it's a bit of hassle. If you plug an internet connection into your Ubuntu machine, then go into Synaptic Package Manager and press Reload, you will get a full package list downloaded to your machine. Then, you can install anything you want.

---


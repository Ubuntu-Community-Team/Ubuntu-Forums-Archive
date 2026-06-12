---
title: "Candido GTK Engine doesn't work!"
date: 2007-02-11
forum: Absolute Beginner Talk
---

### Post by Der Doktor on 2007-02-11
Hi!

I wanna use the [solidLINE GTK Theme]("http://www.roberto-studios.hu/?p=13") which needs the Candido GTK Engine! I have installed the Candido Ubuntu package from [here]("http://candido.berlios.de/") but it doesn't work: :( 
[IMG]http://img246.imageshack.us/img246/2476/candidozc5.png[/IMG]

What can I do?

---

### Post by aidanr on 2007-02-11
i think you need gtk2-engines-pixbuf
sudo apt-get install gtk2-engines-pixbuf

---

### Post by Der Doktor on 2007-02-11
Thanks! :D
Now, the theme works!

---

### Post by fearpi on 2007-04-29
I have the pixbuf engine, but Candido still doesn't work.

Edit: I was using the Ubuntu package on the official site, which doesn't seem to work. Compiling from source with --prefix=/usr does the trick.

---

### Post by olieviya on 2007-08-20
> **fearpi said:**
> I have the pixbuf engine, but Candido still doesn't work.

Edit: I was using the Ubuntu package on the official site, which doesn't seem to work. Compiling from source with --prefix=/usr does the trick.

Hey, I have the same prob as you did, what exactly did you do to make it work?

---

### Post by fearpi on 2007-08-20
Make sure you have the essential build tools. I think the package is build-essential.

Download and extract the engine source code. cd to the extracted directory and do:

```

./configure --prefix=/usr
make
sudo make install
```

---


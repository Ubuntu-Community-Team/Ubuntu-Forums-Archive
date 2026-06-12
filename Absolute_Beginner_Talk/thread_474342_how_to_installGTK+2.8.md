---
title: "how to installGTK+2.8 ?"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by bamesah on 2007-06-15
When I try to install a theme according to this post

[http://dmartin.org/weblog/make-your-ubuntu-desktop-look-slick-with-some-new-gtk-engines-murrine-and-candido](http://dmartin.org/weblog/make-your-ubuntu-desktop-look-slick-with-some-new-gtk-engines-murrine-and-candido)

The terminal says that i need GTK+2.8

I tried to Install it from the site but it need other 3 programs, i installed them and then one of them needed other 2 programs

It got really complicated so I don't know now hoe to install GTK+2.8 ???

---

### Post by odiseo77 on 2007-06-15
GTK 2.10 should be already installed if you're using Gnome, you're probably missing the development libraries or headers needed to compile murrine, so try the following:

```
audo apt-get install libgtk2.0-dev
```

And try to compile the engine again to see what happens... it will probably complaint that you're missing other development libraries/headers;*hint*: if this happens, open synaptic, search for the name of the library you need and in the displayed list, look for a package named something like lib*-dev (where * is the name of the library you're looking for) :)

Greetings.

---

### Post by bamesah on 2007-06-15
> **odiseo77 said:**
> GTK 2.10 should be already installed if you're using Gnome, you're probably missing the development libraries or headers needed to compile murrine, so try the following:

```
audo apt-get install libgtk2.0-dev
```

And try to compile the engine again to see what happens... it will probably complaint that you're missing other development libraries/headers;*hint*: if this happens, open synaptic, search for the name of the library you need and in the displayed list, look for a package named something like lib*-dev (where * is the name of the library you're looking for) :)

Greetings.

When i open the terminal and write ./configure , it tells me that GTK-8.0 is required to compile murrine, i went to synaptic, and GTK is already installed so i don't know what is the problem??

---

### Post by odiseo77 on 2007-06-15
> **bamesah said:**
> When i open the terminal and write ./configure , it tells me that GTK-8.0 is required to compile murrine, i went to synaptic, and GTK is already installed so i don't know what is the problem??

Did you install the development package for GTK as I said in my previous topic?? You **must** do it in order to compile the program.

---


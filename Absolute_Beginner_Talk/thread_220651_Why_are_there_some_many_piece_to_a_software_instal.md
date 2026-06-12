---
title: "Why are there some many piece to a software install?"
date: 2006-07-21
forum: Absolute Beginner Talk
---

### Post by gargoyle on 2006-07-21
Why are there some many piece to a software install?
Example:
Let us say I want to install the program **gnome-ppp**
Not only do I have to down load the program but I also have to download:**
#libatk1.0-0 (>= 1.9.0)
    The ATK accessibility toolkit
#[dep] libc6 (>= 2.3.4-1)
    GNU C Library: Shared libraries and Timezone data
#[dep] libcairo2 (>= 1.0.2-2)
    The Cairo 2D vector graphics library
#[dep] libexpat1 (>= 1.95.8) [powerpc]
    XML parsing C library - runtime library
#[dep] libfontconfig1 (>= 2.3.0)
    generic font configuration library (shared library)
#[dep] libglade2-0 (>= 1:2.5.1)
    library to load .glade files at runtime
#[dep] libglib2.0-0 (>= 2.10.0)
    The GLib library of C routines
#[dep] libgtk2.0-0 (>= 2.8.0)
    The GTK+ graphical user interface library
#[dep] libpango1.0-0 (>= 1.12.2)
    Layout and rendering of internationalized text
#[dep] libx11-6
    X11 client-side library
#[dep] libxcursor1 (>> 1.1.2)
    X cursor management library
#[dep] libxext6
    X11 miscellaneous extension library
#[dep] libxfixes3
    X11 miscellaneous 'fixes' extension library
#[dep] libxi6
    X11 Input extension library
#[dep] libxinerama1
    X11 Xinerama extension library
#[dep] libxml2 (>= 2.6.24)
    GNOME XML library
#[dep] libxrandr2
    X11 RandR extension library
#[dep] libxrender1
    X Rendering Extension client library
#[dep] wvdial
    PPP dialer with built-in intelligence
#[dep] zlib1g (>= 1:1.2.1)
    compression library - runtime 
[/I]

Why is  this? Why are there some many pieces?

---

### Post by Sef on 2006-07-21
They are dependencies and if you use synaptic or the command line, they will automatically install.

---

### Post by gargoyle on 2006-07-21
Yes I know they are dependencies.
The question is why are they not just bundled into the program why are they separate piece?

I just do not understand why it has to be so complex. If they are need why not just package them into the program.

It seems it like buying a car and the salesman asking would you like 4 wheels and tires? If course otherwise how would it run.

---

### Post by Sef on 2006-07-21
Because more than one application may use that dependency.  It's more like buying a from a car manufacturer.  They may have several different makes where the body styles are different, but underneath the body, they are the same.

Just as it is simpler for the car manufacturers to use one chasis style for several car makes, it is simpler for the software developers to use the same dependencies.  Saves a lot of time and space on your computer.

---

### Post by Stew2 on 2006-07-21
So I guess synaptic basically checks when you go to install a program to see if you already have the dependencies satisfied from other programs, and if you don't it prompts you to install the dependencies as well, thus saving the space of repeating the same dependencies for multiple programs?

---

### Post by Sef on 2006-07-21
> So I guess synaptic basically checks when you go to install a program to see if you already have the dependencies satisfied from other programs, and if you don't it prompts you to install the dependencies as well, thus saving the space of repeating the same dependencies for multiple programs?

That is correct.

---

### Post by IYY on 2006-07-21
```
It seems it like buying a car and the salesman asking would you like 4 wheels and tires? If course otherwise how would it run.
```

If you want a valid analogy... Suppose you want to bake a cake. You go to a store and buy all the materials for the cake, whatever they may be. But there are other things you need to make your cake: an oven, a pan, electricity in your house for the oven, a fridge to store the cake in while it cools, a plate and some forks... But the oven may also be used to cook chicken and the plates can be used to eat rice of. 

Apple or Microsoft would package everything when you buy the cake supplies, including an oven, fridge and plates. Note that the fridge and oven are far heavier than the cake itself! Linux is smarter: you may already have an oven in your house, so Synaptic checks for it. If the oven is there, it uses it. Otherwise, it gets you a new one. That way, you don't end up with 1000 ovens on your system and have small downloads.

---

### Post by OU812 on 2006-07-22
You don't come accross this issue very often in windows, but it does happen. There are several programs that have two versions. For example, you can get opera and ooo with or without java - depending upon whether java is already installed on your system or not. Another example is mp3 gain. Available with or without visual basic - for the same argument as above (except vb instead of java).

Likewise, there are some programs in linux that do come bundled with the required dependencies. DVD95 comes to mind.

john

---


---
title: "Update GTK"
date: 2006-12-13
forum: Absolute Beginner Talk
---

### Post by derPilot on 2006-12-13
I´m working with linux/ubuntu since 2 weeks.
So perhaps the solution of my problem is very simple.

I compiled and installed the game TaSpring, which was no problem.
But when I wanted to start the multiplayer lobby called Unity, it tells me that I need
GTK 2.10.0 and PyGTK 2.10.0
```
Error: UnityLobby requires at least GTK v2.10.0 and PyGTK v2.10.0, your versions of GTK and PyGTK are (2, 8, 20)  and  (2, 8, 6)
```
In the moment there seems to be no later version in the repositories of GTK.

So i get gtk+-2.10.0.tar.gz from [http://www.gtk.org/](http://www.gtk.org/) and tried to install it.

I noticed, that i had to install some dependencies and installed and installed...

First problem appeared with glib-2.12.0. After installing this, another program told me, that i should uninstall the old version of glib, because it wouldn´t find the actual version etc..

I found a solution for that.

Later i had to install pango-1.14.0. And everything seemed ok.
But after running ./configure at gtk, it tells me that pango is not installed.
```
*** Pango not found. Pango built with Cairo support is required
*** to build GTK+. See http://www.pango.org for Pango information.
```

Now, after some hours of trying and trying I ask you, if there is a more easy way to get GTK v2.10.0 to work.
Is there a .deb file anywhere for it?
:( 

Thanks for helping me.

---

### Post by Kobalt on 2006-12-13
I'm not sure there's another way of installing the brand new GTK appart from compiling it from the sources... And I'm guessing that shouldn't be easy. 
If I had to, I wouldn't do it... :/
One thing you could do is to check that you installed also the "-dev" packages for your dependencies, these are the ones often missing for compiling stuff...

---


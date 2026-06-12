---
title: "Difference on making a linux app and a win32 app."
date: 2006-05-29
forum: Absolute Beginner Talk
---

### Post by Solidad on 2006-05-29
im taking up Computer Engineering. im quite intrigue.. on the difference in making a linux app and a win32 app

---

### Post by adwait on 2006-05-29
If you are talkin about simple command line apps, no difference. If you are talking GUI, then yeah, theres a difference. In c++ you don't include windows.h, insteak you have the gtk.h

---

### Post by Solidad on 2006-05-29
im sure visual studio 9 doesnt have a gtk.h library.

---

### Post by mostwanted on 2006-05-30
Gtk+ is available for Windows, so yes it does. You just need to install it yourself.

---

### Post by az on 2006-05-30
[QUOTE=Solidad]im taking up Computer Engineering. im quite intrigue.. on the difference in making a linux app and a win32 app[/QUOTE]
In linux, you will be using the GNU toolchain.  So, the development tools are different and the licencing is different.  The principle of free-libre open source software is that the software is not someone else's property.

You have an extensive choice of programming languages and environments in linux, with some in common with win32.

You have a different API for most things, and different shared libraries.

There is a lot that is different.

---

### Post by Solidad on 2006-05-30
how come no one taught us. how to make an app on linux. i guess it self learn for it.

---

### Post by az on 2006-05-30
[QUOTE=Solidad]how come no one taught us. how to make an app on linux. i guess it self learn for it.[/QUOTE]
It depends on your school.  Unix (and linux) application development is quite prominent.

---

### Post by psusi on 2006-05-30
I'm going to assume that your school ( like most ) only teaches you basic standard C/C++ with no win32 api specifics.  As such, C/C++ is C/C++ on any platform, so the code will be the same.  If you are used to using MSVC or some such, then you will just need to learn to use the gnu compiler tools to build your project under linux from the command line.

---

### Post by Solidad on 2006-06-02
yeah THEY did only taught me the basics and not making win32 apps. w/c i don't have a single clue on making one. except making the source code.

---


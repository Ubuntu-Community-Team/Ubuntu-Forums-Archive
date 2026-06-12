---
title: "Dependencies??"
date: 2005-09-04
forum: Absolute Beginner Talk
---

### Post by PenguinsPal on 2005-09-04
Why does everything you want to use have dependencies?
And why don't programs download whatever they need ?

---

### Post by az on 2005-09-04
That's life.  In other operating systems, they resolve their dependancies (Every OS uses shared libraries) easily because you have no choice.  There is only one way to do things.  

In open source software, there are so many different combinations of software that you just have a versioning system and dependancies within that.  So If I write an application that depends on a particular library, I will make the application need today's version (or later) when you compile it.

Packages are precompiled so you do not have to compile it yourself.  Although you could.

Since you have the convenience of using prebuilt binaries, you must life with the limitations that they were build using certain versions of certain shared libraries.

Anyway, the package manager takes care of all tat for you.  All you have to do is enable a proper repository in Synaptic and click on what you like.

---


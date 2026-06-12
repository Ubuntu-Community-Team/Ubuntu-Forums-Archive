---
title: "Konqueror - file order by name"
date: 2007-04-17
forum: Absolute Beginner Talk
---

### Post by ofb on 2007-04-17
In Konqueror, file order by name is a little odd, and I'm wondering what that's about, and if it can be fixed.

For example:

foo
foo2
foo 2
foo_2

But when the files have extension:

foo 2.html
foo_2.html
foo2.html
foo.html

Why does it (mostly) invert the order for files with extension?

----
Just for example variety, this is the result with suffix but no extension:

foo2test
foo 2test
foo_2test
footest

And when all of that is together:

foo
foo2
foo 2
foo_2
foo 2.html
foo_2.html
foo2.html
foo2test
foo 2test
foo_2test
foo.html
footest

---

### Post by leibowitz on 2007-04-29
Maybe that's why they are replacing Konqueror with Dolphin for the KDE file manager.

The problem is related to either the Qdir thing (I don't remember the name), that is the component used by Konqueror to see your directory content. It's this thing that handles the sort, which is a combination of some bits.

Or maybe related to Konqueror itself. But I doubt that. 

That's why I would advice to try with another K-application that is using the same component of QT libraries, to see if you get the same behavior. Then you would know that it is a QT behavior. May be that's not a bug at all, but a feature (TM).

---


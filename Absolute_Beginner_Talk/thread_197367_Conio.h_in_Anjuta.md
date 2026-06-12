---
title: "Conio.h in Anjuta"
date: 2006-06-15
forum: Absolute Beginner Talk
---

### Post by jeanvial on 2006-06-15
Hi.

How can I include or use the conio.h library on Anjuta?

Thank´s.

:-({|=

---

### Post by Hanj on 2006-06-15
I might be wrong, but I think conio.h is a Borland specific header. Don't think you can use it under linux (someone correct me if I'm wrong, please). What function do you need from it? There's probably some linux equivalent.

---

### Post by jeanvial on 2006-06-15
Yes but what are these library?

Or on which other IDE can I programing in c?(that including these library)

---

### Post by Hanj on 2006-06-15
> Yes but what are these library?I don't think there's *one* lib that replaces conio.h, but if you could just say what you need it for, maybe someone can tell you of a linux equivalent to that function. 

In fact, I only used conio.h once (way back in time) and that was for a function called getch (which would wait for a key to be pressed and then return the scancode of the key). If you're after something like that, maybe [Ncurses]("http://www.tldp.org/HOWTO/NCURSES-Programming-HOWTO/index.html") could work? I've never used it myself but it seems to be able to do similar things (and much more).

And it's not the IDE that determines which libraries you can use. Anjuta just lets you edit and manage the source code, it uses gcc to do the actual compiling (as does all Linux IDEs (that I know of at least)), so changing IDE won't affect which libs you can use.

---


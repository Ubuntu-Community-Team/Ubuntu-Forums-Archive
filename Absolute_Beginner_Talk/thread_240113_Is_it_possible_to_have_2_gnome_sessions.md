---
title: "Is it possible to have 2 gnome sessions?"
date: 2006-08-20
forum: Absolute Beginner Talk
---

### Post by jincast90 on 2006-08-20
I would like to have 2 gnome sessions, becouse I would like to have a session which is bassicly a clone of macosx, but I would still like to have the session, I am using right now.

---

### Post by The Uniphobiac on 2006-08-20
I know that it is possible with dual monitors or tvout.

---

### Post by jincast90 on 2006-08-20
> **The Uniphobiac said:**
> I know that it is possible with dual monitors or tvout.

But I would like it to be possible to choose it at login, like you can do with kde and xfce.

---

### Post by kebes on 2006-08-20
Idea #1:
You could set up two different user accounts with their own unique preferences, including visual styles, etc.

You could even make the two users part of the same group so that they would have access to the same user files.

I know that's not a very elegant solution, but it should work.


Idea #2:
The command that starts up your desktop is "gnome-session". If you look up it's manual page "man gnome-session":
[http://www.die.net/doc/linux/man/man1/gnome-session.1.html](http://www.die.net/doc/linux/man/man1/gnome-session.1.html)

There is a "--choose-session=ARG" that allows you to select what session you want. I assume this allows you to override the default configuration file and use a different file. You could play around with that. I've never done it but it looks like it should work.

---


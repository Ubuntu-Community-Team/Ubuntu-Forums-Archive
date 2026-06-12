---
title: "Error at login."
date: 2006-06-16
forum: Absolute Beginner Talk
---

### Post by Torquemada28 on 2006-06-16
Just before the KDE login box appears, I have an error message pop up.

"Cannot parse theme file /usr/share/apps/kdm/themes/kubuntu"

As far as I can tell, whatever this error message relates to has no impact on anything. All the same, I'd like to fix the problem just because it irks me everytime I boot up.

What does this error mean, and more importantly, how should I go about fixing it?

---

### Post by u.b.u.n.t.u on 2006-06-16
Just a guess,

"Cannot parse theme file /usr/share/apps/kdm/themes/kubuntu"

seems you have a corrupted file(s) or path.

Go there and have a look. You might see something odd.

It seems the error message means that ubuntu is told to load that theme but can't.

I use gnome so I can't see if that is a default or custom folder.

---

### Post by Torquemada28 on 2006-06-16
[QUOTE=u.b.u.n.t.u]
Go there and have a look. You might see something odd.
[/QUOTE]
The folder exists but it's empty.
Looks like I found "something odd".;)

---

### Post by xenblend on 2006-06-16
You might try 'dpkg-reconfigure kdm' to reconfigure the K display manager...

---


---
title: "no shutdown, restart buttons in compiz"
date: 2006-08-10
forum: Absolute Beginner Talk
---

### Post by shanepardue on 2006-08-10
i've heard it's because i installed compiz on it's own session just in case things didn't work out. i later made it the default session, but it's still missing those buttons.

if it involves removing compiz and reinstalling it as a permanent thing then i will.

what do you think?

---

### Post by MarkSheely on 2006-08-10
Which method did you use to install xgl/compiz?

--Mark

---

### Post by shanepardue on 2006-08-10
> **MarkSheely said:**
> Which method did you use to install xgl/compiz?

--Mark
i don't remember which thread i followed, but i know i have a separate session for whenever i want to use compiz (which is now set as default)

---

### Post by MarkSheely on 2006-08-11
Hmmmm.....I honestly can't say what the problem could be without seeing the installation method you used.  I can tell you that this is a problem alot of people run into, and from what I can tell, they often end up using a different installation method.

Good luck, and I'm sorry I couldn't help you more.
--Mark

P.S. If you want, let me know what kind of graphics card you have, and I can try to point you in the direction of a method which should work without much hassle.

---

### Post by tomtom_in_eire on 2006-08-11
Hey,
That's actually because you are using Compiz in a session.
In other words, that's like running ubuntu with gnome, and compiz on top of that.
Of course, you don't see the buttons becaouse all you don't have any control over the gnome session. You need first to close the compiz session, then you can control gnome.

I hope this is understandable, anyway, the import thing to note is that what you see is normal.

If you want to see the stop / restart buttons, try using compiz with aiglx. there are a couple of posts about that on the internet.

good luck.

---

### Post by shanepardue on 2006-08-11
that makes sense..so i have to use the gnome session and just have compiz installed on that session. i'm a little lost on how to make that so. any push towards the right direction would be great! thanks guys!

---

### Post by MarkSheely on 2006-08-11
When it is time to log out or shutdown your computer, enter: 

metacity --replace

into the terminal.  This should stop compiz, and you should then be able to shutdown/logout normally.  

Give it a try, and let us know how it works.

Good luck,
Mark

---

### Post by shanepardue on 2006-08-12
> **MarkSheely said:**
> When it is time to log out or shutdown your computer, enter: 

metacity --replace

into the terminal.  This should stop compiz, and you should then be able to shutdown/logout normally.  

Give it a try, and let us know how it works.

Good luck,
Mark
nope that doesn't work.

---


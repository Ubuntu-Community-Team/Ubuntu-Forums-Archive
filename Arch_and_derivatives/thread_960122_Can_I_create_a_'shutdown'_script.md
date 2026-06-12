---
title: "Can I create a 'shutdown' script?"
date: 2008-10-27
forum: Arch and derivatives
---

### Post by whitefort on 2008-10-27
Sorry for another such noobish question.

I presume Arch has a shutdown script of stuff that needs to be done before a shutdown?

I was wondering if there was any way to add one of my own.  For example, in the course of a day I manage to fill a few 'junk' folders with various stages of work-in-progress.  At the end of the day, I move the versions I want to keep to a 'proper' folder, and delete all the others.

I was just wondering if there's a way I could set up a little script (basically doing a 'rm *.*' on the contents of the junk folders) that would always execute on shutdown (or even better, every time I log out)

If not, I'll still make the script and run it by hand, but I'm sure Arch has an easy way to automate this sort of thing?

Thanks!

---

### Post by mips on 2008-10-27
Yes you can but it depends on your environment. Are you using a desktop/window environment and which one? Do you login via bash, gdm, kdm etc and which one?

---

### Post by whitefort on 2008-10-27
Thanks for the reply - I've already learned something, as I didn't know it would depend on the environment!

Or does it just depend on the environment if I want a logout script?

Anyway, I've set up to log in via gdm, and I spend most of my time in Gnome.

Thanks!

---

### Post by mips on 2008-10-27
Just put the script you want to execute (runs as root) in
```
/etc/gdm/PostSession
```

You could just backup the Defualt one and edit the original it without creating a new script. backup is just for reference purposes.

---

### Post by whitefort on 2008-10-27
Great - that's exactly the info I was looking for - thanks!

---

### Post by Barrucadu on 2008-10-27
Also, if you want something to run on shutdown, put it in /etc/rc.local.shutdown

---


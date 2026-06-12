---
title: "kubuntu to ubuntu to kubuntu?"
date: 2006-06-05
forum: Absolute Beginner Talk
---

### Post by not_yet on 2006-06-05
I have the standard ubuntu installation with gnome

can I switch to kubuntu to try it out, and back to ubuntu if I don't like it?

thanks

---

### Post by Gannin on 2006-06-05
Yes.  Use Synaptic to install kubuntu-desktop.

---

### Post by not_yet on 2006-06-05
ok kubuntu-desktop installed

how do I switch back and forth

thanks

---

### Post by aysiu on 2006-06-05
Log out.
Select **Session**.
Select **KDE**.
Log in.

And if you want to remove Kubuntu later, good luck, since you installed it with Synaptic instead of *aptitude*.

---

### Post by not_yet on 2006-06-05
hummmm....... kde is not an option:confused:

---

### Post by aysiu on 2006-06-05
[QUOTE=not_yet]hummmm....... kde is not an option:confused:[/QUOTE] So you don't get this?

---

### Post by not_yet on 2006-06-05
everything except the kde

---

### Post by richbarna on 2006-06-05
[QUOTE=aysiu]Log out.
Select **Session**.
Select **KDE**.
Log in.

And if you want to remove Kubuntu later, good luck, since you installed it with Synaptic instead of *aptitude*.[/QUOTE]

Yup !, something to remember.
If you install a desktop environment, ALWAYS do it with aptitude, a hell of a lot easier to remove.

---

### Post by localzuk on 2006-06-05
Why will it be difficult to remove? Is it due to it being a meta package?

---

### Post by localzuk on 2006-06-05
Try running 'sudo aptitude install kubuntu-desktop' from a terminal. What does it do?

---

### Post by dux on 2006-06-05
I'm trying to give KDE a try, but when I try to install Kubuntu-desktop it brings up a massive list of dependencies, do I have to go through installing them all by hand?

---

### Post by richbarna on 2006-06-05
okay, so try :-
> sudo apt-get update
then :-
> sudo aptitude install kde

---

### Post by dux on 2006-06-05
```
No solution found within the allotted time. 
``` :???:

---

### Post by Gannin on 2006-06-05
Perhaps he meant:

```

sudo aptitude install kde-desktop

```

I'm not familiar with aptitude. Why does installing with it make removing groups of packages later on more easy?

---

### Post by urbanmyth on 2006-06-05
hi, I'm a noob myself, but wouldn't it be easier to select kde desktop in synaptic and let it install dependencies? :-k  I've done this in the past when I mistakenly thought KDE was for me....

---

### Post by aysiu on 2006-06-05
For the whole deal, including aptitude v. apt-get:
[http://www.psychocats.net/ubuntu/kde.html](http://www.psychocats.net/ubuntu/kde.html)

---

### Post by Ptero-4 on 2006-06-05
The reason aptitude is easier than synaptic/apt-get is b/c it keeps track of the dependencies and can do reverse dependency handling (removing packages marked as dependencies when the package that marked them is removed). This means that if you install a package with aptitude, when you remove it, all the packages that got installed are also removed. Apt-get OTOH leave them lying around.

---

### Post by Gannin on 2006-06-06
Very good information.  Thank you.

---


---
title: "Server install with X server"
date: 2008-03-23
forum: Absolute Beginner Talk
---

### Post by saj0577 on 2008-03-23
Hey,

What is the best way to get a minimalistic install (server edition) but with an X server.
So i don't want any of the open office of any of those programs you get with Ubuntu desktop i just want a Ubuntu server edition install with a x server. What is the best way of doing this?How?


Thanks in advance
Saj

---

### Post by iansane on 2008-03-23
I've just posted similar question but need gnome desktop and nvidia drivers for 64 bit server so maybe we'll both get some help :-)

---

### Post by saj0577 on 2008-03-23
Yeah.

I want to basically have a ubuntu desktop install but without any programs. (apart from terminal)

Saj

---

### Post by ghost_ryder35 on 2008-03-23
install the ubuntu server edition
and then 
```

sudo aptitude update && sudo aptitude install xubuntu-desktop 

```
I belive this should work :)

---

### Post by iansane on 2008-03-23
Ok I see you already found the other post but for anyone else, see this:

[http://ubuntuforums.org/showthread.php?t=733097](http://ubuntuforums.org/showthread.php?t=733097)

Or as post above says xfce-desktop instead of ubuntu-desktop I guess?

---

### Post by saj0577 on 2008-03-23
> **ghost_ryder35 said:**
> install the ubuntu server edition
and then 
```

sudo aptitude update && sudo aptitude install xubuntu-desktop 

```
I belive this should work :)

That will add all the xubuntu desktop edition programs to which i dont want i just want a graphical interface for my server.

Saj

xserver-xorg?? Wil that do the job?

---

### Post by ghost_ryder35 on 2008-03-23
> **saj0577 said:**
> That will add all the xubuntu desktop edition programs to which i dont want i just want a graphical interface for my server.

Saj

xserver-xorg?? Wil that do the job?

You could remove all the programs once it installs....
that only installs the server, then you need something like xfce,gnome,kde etc....

---

### Post by saj0577 on 2008-03-23
> **ghost_ryder35 said:**
> You could remove all the programs once it installs....
that only installs the server, then you need something like xfce,gnome,kde etc....

Safe to remove the programs are none of them "needed"?

Saj

---


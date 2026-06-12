---
title: "Ubuntu Splash change?"
date: 2006-12-23
forum: Art &amp; Design
---

### Post by Fittersman on 2006-12-23
how do i use the ubuntu splash theme in edgy?

the one i want to use is in theis link:

[http://gnome-look.org/content/show.php?content=44531](http://gnome-look.org/content/show.php?content=44531)

---

### Post by hikaricore on 2006-12-24
That's a splashy theme, you'll have to install splashy.

This is not the same thing as the ubuntu splash screen.

There's actually a link on the page you linked for into about installing splashy.

If that doesn't help you, try this: [http://splashy.alioth.debian.org/wiki/doku.php?id=faq](http://splashy.alioth.debian.org/wiki/doku.php?id=faq)

---

### Post by Fittersman on 2006-12-25
ok, I got to this part:

```
cleippi@cleippi-desktop:~$ sudo apt-get install splashy splashy-themes
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package splashy

```

and thats what happened, what should i do? I'm not sure if this is done or not, where do i put it?

```
Make sure that you have “vga=791 splash” as kernel parameters. You can add this to /boot/grub/menu.lst or /etc/lilo.conf. See the FAQ section for more.
```

It just says that i should add that vga=791 splash in there but i dont know where to add it or if its already done.

---


---
title: "Installed FreeBSD, and it's rather confusing."
date: 2008-06-10
forum: BSD
---

### Post by Barrucadu on 2008-06-10
I decided to take my first steps into BSD-land today, since I have an old laptop here that had no purpose. I installed FreeBSD, and it is different to say the very least.
I'm sure I'll have loads of fun with it :)

---

### Post by ibutho on 2008-06-10
You'll definitely have loads of fun. I remember my first FreeBSD installation and how I was completely baffled by its differences with Linux. The [FreeBSD Handbook]("http://www.freebsd.org/doc/en_US.ISO8859-1/books/handbook/index.html") proved to be a very valuable resource.

---

### Post by Barrucadu on 2008-06-10
I'm writing this reply from FreeBSD, so I have at least figured out how to install Openbox and Opera, if nothing else. :lol:
Over the next few days I'll be installing and configuring everything I need to use it properly, then after that it's time to dig beneath the surface.

---

### Post by cardinals_fan on 2008-06-10
> **Barrucadu said:**
> I'm writing this reply from FreeBSD, so I have at least figured out how to install Openbox and Opera, if nothing else. :lol:

Feel lucky.  Opera hates NetBSD :(

---

### Post by cammin on 2008-06-11
> **cardinals_fan said:**
> Feel lucky.  Opera hates NetBSD :(

Is that because NetBSD doesn't want a closed source binary, or because Opera doesn't want to develop a NetBSD version?

---

### Post by swoll1980 on 2008-06-11
I tried freebsd I installed gnome but couldn't for the life of me figure out how to configure it right. I got to the point that I could startx and run programs from the terminal gnome-panel for instance and it was functional, but I couldn't get over the hump. Perhaps I will try it again sometime soon. I will add that it seemed very fast and responsive. I tried pc-bsd it was definitely faster than Linux though I can't stand kde. pc-bsd has a cool tool that works like install shield it's got some potential

---

### Post by Barrucadu on 2008-06-11
I've made ports a bit more like a Linux package manager by creating three scripts in /usr/local/bin (I'm getting the hang of the directory structure, too): *ports-update*, *ports-install*, and *ports-remove*. Only really simple scripts, but they make life a little easier. Next, is a *ports-search* script!

---

### Post by cardinals_fan on 2008-06-11
> **cammin said:**
> Is that because NetBSD doesn't want a closed source binary, or because Opera doesn't want to develop a NetBSD version?
The latter.

That's why I dual-boot NetBSD with Slackware :)

---

### Post by Bachstelze on 2008-06-11
> **cardinals_fan said:**
> The latter.

That's why I dual-boot NetBSD with Slackware :)

They're not developing a FreeBSD version either, FreeBSD uses the Linux version through its Linux compatibility layer. But it's true that NetBSD's is far less advanced...

---

### Post by cardinals_fan on 2008-06-11
> **HymnToLife said:**
> They're not developing a FreeBSD version either, FreeBSD uses the Linux version through its Linux compatibility layer. But it's true that NetBSD's is far less advanced...
No, there is a FreeBSD version of Opera.  It doesn't seem to be the one distributed through ports (go figure), but you can download it from their site.

---

### Post by MONODA on 2008-08-31
> I've made ports a bit more like a Linux package manager by creating three scripts in /usr/local/bin (I'm getting the hang of the directory structure, too): *ports-update*, *ports-install*, and *ports-remove*. Only really simple scripts, but they make life a little easier. Next, is a *ports-search* script!
any chance you could provide us with those? :)

---

### Post by sandysandy on 2008-08-31
had installed freeBSD about a month back.

during installation had selected the window maker, gnome packages etc.

but when i boot into freeBSD i only get the text terminal and not the GUI.:(

any help.:)

regards

---

### Post by Bachstelze on 2008-08-31
The GUI isn't started by default. Try

```
/usr/local/etc/rc.d/gdm start
```

---

### Post by MONODA on 2008-08-31
or just startx

---

### Post by Bachstelze on 2008-08-31
> **MONODA said:**
> or just startx

No. By default, [FONT="Courier New"]startx[/FONT] will just start the X server, with no window manager whatsoever.

---

### Post by MONODA on 2008-08-31
> No. By default, [FONT=Courier New]startx[/FONT] will just start the X server, with no window manager whatsoever.
are you sure, because I remember that just typing in startx will start an X server with the wm/de that you installed during the freebsd installation. I assume that it automatically creates a .xinitrc during installation. (Then again I could be totally wrong since I dont use freebsd now.)

---

### Post by mips on 2008-09-01
> **MONODA said:**
> are you sure, because I remember that just typing in startx will start an X server with the wm/de that you installed during the freebsd installation. I assume that it automatically creates a .xinitrc during installation. (Then again I could be totally wrong since I dont use freebsd now.)

I'm pretty sure from recollection that only X will be started. Had to manually edit xinitrc.

---


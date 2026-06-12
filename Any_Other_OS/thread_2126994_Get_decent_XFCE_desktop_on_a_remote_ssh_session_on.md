---
title: "Get decent XFCE desktop on a remote ssh session on a Mac workstation?"
date: 2013-03-18
forum: Any Other OS
---

### Post by 1clue on 2013-03-18
Hi,

I have a Mac, which is my work system.  I have a Linux box which is both work and personal, meaning that I've found it convenient to move some of my work functionality over there.

I frequently **ssh -X myXubuntuBox** and then start an X app which displays on my mac.

I'd like to be able to get a session which seems like remote desktop.  This would contain my Xubuntu window manager and settings, rather than the Mac's half-@$$ attempt at an X11 implementation.

Moreover, I believe this should be able to be done using xorg, not remote desktop or xvnc.

I've been playing with Xnest but haven't got it to even open a window.

Any help would be appreciated.

Thanks.

---

### Post by mips on 2013-03-19
Like this [http://narnia.cs.ttu.edu/drupal/node/132](http://narnia.cs.ttu.edu/drupal/node/132) ?

---

### Post by 1clue on 2013-03-19
Thanks, but that's not what I'm after.  For me, btw, it's xfce4-session.  That process gets a bunch of Mac windows on a Mac desktop, and some poorly laid out widgets, which are all half-usable.

I want to divorce the Mac window manager from everything, like something similar to what Remote Desktop gives you:  A window containing a desktop, and whose contents are ENTIRELY drawn by the Linux box.

I'm on the right track now.  I can get a non-secure Xnest from my mac, **Xnest -query 192.168.1.100 geometry 1920x1080** gives me the window I want, I'd like to get that secure but that's something I think I can handle.

Thanks.

---

### Post by 1clue on 2013-03-19
I can get "secure" but unusable Xnest like this:
```

ssh -X 192.168.1.100
<password>
Xnest :1 -geometry 1920x1050 -query localhost

```

Which gives me a window containing a login screen.  The problem is, the keyboard is gobbledygook.

The bottom of the man page, "FUTURE DIRECTIONS", gives me little hope:
> Perhaps there should be a command-line option to tell Xnest to inherit the keyboard and pointer control parameters from the real server rather than imposing its own.

I'd rather have this all be secure given that it can under some circumstances be over wireless, but for now I guess I have something that will work.

Thanks.

---

### Post by 1clue on 2013-03-19
OK, I guess I have no solutions.  The keyboard is messed up no matter how I use Xnest.

---


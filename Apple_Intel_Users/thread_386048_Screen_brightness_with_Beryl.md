---
title: "Screen brightness with Beryl"
date: 2007-03-16
forum: Apple Intel Users
---

### Post by jeffro on 2007-03-16
Hi, I have Ubuntu Edgy running on my Macbook.  I followed the tutorials and everything and got all the basic stuff working, I also recompiled my kernel to get some better trackpad support (so I can turn it off when I plug a mouse in) but I'm having an issue with the screen brightness keys.  They work fine when I select Metacity as my window manager but not when I'm using Beryl.  Is there a work around to solve this problem, or is it just something I should learn to deal with?  Thanks for any help.

---

### Post by dannyboy79 on 2007-03-16
have you tried any of this?
[http://felipe-alfaro.org/blog/2006/09/11/modifying-screen-brightness-on-ac-state-changes/](http://felipe-alfaro.org/blog/2006/09/11/modifying-screen-brightness-on-ac-state-changes/)

---

### Post by jeffro on 2007-03-16
I hadn't seen that, I'll give it a try.  Thanks!

---

### Post by jeffro on 2007-03-16
Well it didn't fix my problem.  Though apparently my problem isn't really with the brightness keys, I think it's that Beryl is interfering with the bindings.  Until I figure something out I can just run macbook-brightness from the command line.

---

### Post by das_syndrom on 2007-03-17
Hi!

Beryl uses its own key bindings.

1. Open the Beryl Settings Manager
2. -> General Options -> General Options -> Commands
3. Edit Command Line 1: (for me: /usr/bin/macbook-backlight -10)
and Command Line 2 (/usr/bin/macbook-backlight +10)
4. -> General Options -> Shortcuts -> Keyboard and Mouse
5. Run Command 1 -> Grab Key -> press F1 (or Fn+F1)
Run Coomand 2 -> Grab Key -> press F2 (or Fn+F2)
6. Save
7. Enjoy (hopefully... :-) )

Andi

---

### Post by jeffro on 2007-04-08
That did it for me, gracias.

Jeff

---


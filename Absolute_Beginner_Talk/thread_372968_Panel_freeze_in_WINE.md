---
title: "Panel freeze in WINE"
date: 2007-02-28
forum: Absolute Beginner Talk
---

### Post by freebird54 on 2007-02-28
I've been cruising the web and forum posts for while now, and see no reference to this particular problem...

I start up a WINE assisted program or 2, and they work wonderfully well (amazing idea/implementation so far!)  BUT after a while the upper and lower panels freeze solid - and of course the programs etc that I normally access from there are unavailable (including shutdown!)

CTRL-ALT-BS resets the X session, but a complaint from the 'incoming' panel claims that one is already running - so it does not install.  This leaves me with only a desktop terminal to type 'shutdown -r 1' in......

Anyone else run into this one?  Better ways out?  just run different programs?

Thanks for any help/ideas out there.

BTW: - don't worry about posting stupid ideas - I have lots of them - and some of them work!

---

### Post by energiya on 2007-03-01
When Gnome seems to freeze, go to tty1 (or what you like) and type
```

top

```
and see the CPU usage (this is probably the cause for freezing). You can kill from there the problem-makers, or use "killall".

I also recommend using [htop]("http://htop.sourceforge.net/") over top (much nicer).

---


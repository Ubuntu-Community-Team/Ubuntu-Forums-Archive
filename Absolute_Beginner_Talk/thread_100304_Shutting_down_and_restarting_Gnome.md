---
title: "Shutting down and restarting Gnome"
date: 2005-12-07
forum: Absolute Beginner Talk
---

### Post by Granduke on 2005-12-07
I have a old box.  Can I start programs like a Bittorrent client,  then shut down GNOME overnight to save resources and restart it again in the morning? If possible, what would be the procedure?

---

### Post by earobinson on 2005-12-07
I do not think so, you could run fluxbox, or xubuntu (they use less resources than gnome) you could also boot into the comand line and use the command line bittorrent tools.

But the bittorrent program you are using needs a gui so I think it needs gnome (or some other desktop env) to suport it.

I could be wrong however this is just my guess

---

### Post by Brunellus on 2005-12-07
You want a commandline bittorrent client, as described [here](http://www.cyberciti.biz/nixcraft/vivek/blogger/2005/03/linux-command-line-bittorrent-client.html).

It'd be possible to just exit to a commandline from your graphical session, but to do so you'd have to dispense with GDM, the graphical display manager (the gui login screen).

I wonder how much of an actual performance penalty you're paying by simply leaving gnome up and running, though.  You might, as earobinson notes above, want to consider moving to a more lightweight desktop environment like XFCE (that's the X in Xubuntu) or Fluxbox (my personal favorite).

---


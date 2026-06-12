---
title: "SU in GUI?"
date: 2007-06-26
forum: Absolute Beginner Talk
---

### Post by quicksilver1234 on 2007-06-26
Hi All,
When I'm in command line, I can type SU and be able to do stuff to set up my computer but it's clumsy. 
How do I do the equivalent in the Ubuntu Graphical Interface? GUI would be easier.
Thanks,
- John.

---

### Post by freebird54 on 2007-06-26
Not sure why, or what you're after, but gksudo nautilus in a terminal will open a file manager session with you as root.  Be  careful if you do this!  The Law of Unintended Consequences is just waiting for you... :)

---

### Post by xelnaga666 on 2007-06-26
Yeah it would be pretty silly to make changes in a gui.

You could use the method above, or theres the method I used earlier in order to recover some data.

Restart your machine. When GRUB gets to the first stage and says "press ESC if you want to..........etc.......", hit ESC so you can see the boot options. Boot into a recovery kernel.

This will dump you into the cli with root privilages. Just do a "startx" and your default window manager should pop up with root level access.

Again, this is highly NOT recommended. Seriously, these security methods were put in for a reason :P.

---

### Post by p_quarles on 2007-06-26
The above ideas will certainly work, but there's another (and I think safer) way to do this. When you want to run a specific application in root, open a terminal and type: ```
gksu {name-of-app}
```

That will run a graphical application as root, so you can do things like use Gedit to change config files, or whatever, without logging into the entire system as root (which does pose some risks if you aren't sure what you're doing).

---

### Post by handydan918 on 2007-06-26
And whether at CLI or GUI, DO NOT type the "resume' command" (<rm -rdf />). ]
(*,)

---


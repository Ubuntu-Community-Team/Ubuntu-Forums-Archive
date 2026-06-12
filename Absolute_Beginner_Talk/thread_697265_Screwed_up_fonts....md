---
title: "Screwed up fonts..."
date: 2008-02-14
forum: Absolute Beginner Talk
---

### Post by doorknob60 on 2008-02-14
Well, I read this howto in the tutorials section to make my fonts smoother, and I didn't like it, so I tried a bunch of things to undo it but nothing would work. I just need a way to set my settings back to the Ubuntu default.

Heres how it looks:

[IMG]http://i26.tinypic.com/xlky13.png[/IMG]

Here's how I want it to look:

[IMG]http://i27.tinypic.com/2zjbcde.png[/IMG]

NOte that my Firefox is somehow unaffected but everything else is and it's not a big deal but I liked it a lot better how it was, because these fonts have some weird effects on some of the things I do.

---

### Post by emarkd on 2008-02-15
Font settings are under System > Preferences > Appearance.  There's a font tab at the top.  Try changing the rendering method until you find one that suits you.

---

### Post by doorknob60 on 2008-02-15
I tried that, but it didn't work. I'll edit with the command I used to do this.

Here it is: ```
sudo ln -sf /etc/fonts/conf.avail/10-autohint.conf /etc/fonts/conf.d/
```

I tried all the obvious things like undoing the symlink and linking some other files into conf.d that sounded right but nothing changed :(

---

### Post by doorknob60 on 2008-02-15
Bumpity bump bump bump! I gotta go to bed soon, I'll be back tommorow.

---

### Post by doorknob60 on 2008-02-15
Okay I'm back (yay 3 day weekend :D), any ideas?

---

### Post by doorknob60 on 2008-02-16
Bump!

---

### Post by doorknob60 on 2008-02-17
Come on I really need this fixed!

---


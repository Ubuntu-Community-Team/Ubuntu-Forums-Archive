---
title: "conky and gdesklets"
date: 2008-02-07
forum: Absolute Beginner Talk
---

### Post by brokenhachi on 2008-02-07
hey ive got a few Qs about conky and desklets..

ill start with conky..

i'm trying to figure out how to get conky to show on all 4 desktops (like when using compiz)

and with Gdesklets...

im trying to figure out how to get it so that the shortcut buttons screenlet will not have a border around it.. or atleast the whole thing is transparent so all you can see on the screen is the buttons and now the bar.

thanks in advance for the help!

---

### Post by emarkd on 2008-02-07
I'm not sure which of these make Conky do what you want, but I know mine does that, so here's the lines from my .conkyrc that I think effect that:

```

own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

```

Hope that helps.

---

### Post by brokenhachi on 2008-02-07
right that seems to have worked, thanks!


now i just need help with the gdesklets thing.. can anyone lend a hand?

---

### Post by brokenhachi on 2008-02-07
one more... i was wondering how i can make conky below everything.. i tried putting a screenlet on top of it and it got lost under it.....

---

### Post by emarkd on 2008-02-07
Is it just the desklets that give you trouble, or is Conky sitting on top of all of your windows?  I don't use desklets so I don't know if this'll work, but my Conky sessions blend in with the desktop and stay underneath everything.  I've attached one of my .conkyrc's so you can try and see where ours are different.

The forum uploader wouldn't take it without a .txt on the end.

---

### Post by brokenhachi on 2008-02-07
its just desklets and icons.... i dont see any difference in yours and mine, except that im using more information under the text line.. but as far as settings they are basically the same.

---

### Post by emarkd on 2008-02-07
I don't use the desklets, but now that you mention it desktop icons fall behind my Conkies, too.  I keep a pretty clean desktop, so I havent' had that happen in a while and had forgotten.  I'll be watching this thread for a solution along with you.

---


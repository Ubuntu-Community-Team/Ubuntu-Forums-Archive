---
title: "newsticker app?"
date: 2007-08-03
forum: Absolute Beginner Talk
---

### Post by words1 on 2007-08-03
Does anyone know of a Gnome app that acts like a scrolling new sticker, like the old BBC ticker in Windows?  I know there's something in KDE, but it doesn't seem to work in Gnome.

---

### Post by flatwombat on 2007-08-03
[http://gdesklets.zencomputer.ca/](http://gdesklets.zencomputer.ca/)  Try NewsTicker or NewsGrab  These run under Gdesklets, which you can easily install if not already on your system.

---

### Post by words1 on 2007-08-04
excellent -- thanks

---

### Post by aerojad on 2007-12-01
I've been looking for something like this as well and when I install either gdesklet (or try to activate much of any other ones, for that matter) I get an error along these lines:

> No Control could be found for interface INewsGrab:49qghn7jup3s5ydphdw5ooq7d-2
/home/jad/.gdesklets/Displays/NewsTicker/ticker.display

/home/jad/.gdesklets/Displays/NewsTicker/ticker.display                              
>   1 rss = get_control('INewsGrab:49qghn7jup3s5ydphdw5ooq7d-2')

any ideas?

---

### Post by saperduper on 2008-01-16
> **aerojad said:**
> I've been looking for something like this as well and when I install either gdesklet (or try to activate much of any other ones, for that matter) I get an error along these lines:



any ideas?

I had exactly the same problem with the NewsTicker gdesklet and it was solved with the advice i found in this post [HTML]http://forums.fedoraforum.org/showpost.php?p=516249&postcount=2[/HTML]

If you have installed it as a user, open a Terminal and
```
ln -s ~/.gdesklets/Displays/NewsTicker/controls/NewsGrab ~/.gdesklets/Controls/NewsGrab
```

---

### Post by Sabrage on 2008-01-18
I installed gDesklets, and downloaded and extracted the NewsTicker file to my desktop. But how do I install it?

---


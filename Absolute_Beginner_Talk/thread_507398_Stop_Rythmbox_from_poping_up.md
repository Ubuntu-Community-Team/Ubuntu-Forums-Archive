---
title: "Stop Rythmbox from poping up"
date: 2007-07-22
forum: Absolute Beginner Talk
---

### Post by Webby_s on 2007-07-22
I have removed rythmbox from my add/remove application but I still get a box popping up stating that "Couldn't exucute command:Rhythmbox verify that this command exists" And it is extremely annoying.

Now I am serious when I say this..... I think it has to do with the keyboard mapping because every time I press the left, up, or right arrow keys WITH the num lock ON the dialog pops up. So was there some type of quick key that causes rhythmbox to load? Will I need to re-install my keyboard. (I did have to mess around a little with the XORG file for resolution issues.)

---

### Post by wolfen69 on 2007-07-22
system>preferences>removable drives and media>multimedia tab

edit: sorry, i think i misunderstood the question. it may help to uncheck it though. and assign a different player.

---

### Post by Webby_s on 2007-07-23
Ya I did a search on the forum and I read to do the system>preferences>removable drives and media>multimedia tab and nothing changed.

Like I said I think it has to so with some type of keypad mapping problem. Cuz like I discribed it only happens with the arrow keys with num lock on. It is just weird. The obvious 'quick' solution is to turn num-lock off. But I would just like to fix it once and for all. I could also try and change my XORG file again by:

```
sudo dpkg-reconfigure xserver-xorg
```

---


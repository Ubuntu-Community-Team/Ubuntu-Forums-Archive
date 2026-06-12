---
title: "Mplayer options ???"
date: 2006-07-24
forum: Absolute Beginner Talk
---

### Post by MaximB on 2006-07-24
1.I love MPlayer - but I can't see were I select the options and preferences ?
2.I want that my screensaver won't show off when I'm playing movies with MPlayer (like in totem) , how ?

---

### Post by Hallavej on 2006-07-24
You put them in $HOME/.mplayer/config
See
mplayer --help
and
man mplayer
for options. Example, vo=xv will make xv the default video output.

---

### Post by geco on 2006-07-24
> **MAXDDARK said:**
> 1.I love MPlayer - but I can't see were I select the options and preferences ?
2.I want that my screensaver won't show off when I'm playing movies with MPlayer (like in totem) , how ?

here is an example of $HOME/.mplayer/config

```

#Video Driver
vo= gl2,sdl,x11,
#Audio Driver
ao=alsa,oss,sdl,
#Disable Xscreensaver
stop-xscreensaver=true

```

anyway the best to do is
```

man mplayer

```

---

### Post by AndyCooll on 2006-07-24
Not used mplayer for awhile.

When you open up mplayer does it not open up as two sections?

And if you right-click on the "videoscreen" section isn't one of the options in the list that pops up "preferences"?

:cool:

---

### Post by taurus on 2006-07-24
> **AndyCooll said:**
> Not used mplayer for awhile.

When you open up mplayer does it not open up as two sections?

And if you right-click on the "videoscreen" section isn't one of the options in the list that pops up "preferences"?

:cool:
Mplayer is a text base media player while gmplayer is the GUI that you are talking about...

---

### Post by MaximB on 2006-07-24
> **AndyCooll said:**
> Not used mplayer for awhile.

When you open up mplayer does it not open up as two sections?

And if you right-click on the "videoscreen" section isn't one of the options in the list that pops up "preferences"?

:cool:

All good now...thanx !

---


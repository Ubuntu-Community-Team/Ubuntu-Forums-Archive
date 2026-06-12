---
title: "desktop disappeared after &quot;restarting&quot; firefox"
date: 2007-02-04
forum: Absolute Beginner Talk
---

### Post by xSauronx on 2007-02-04
using Xubuntu 6.10 on an Inspiron 1000

i was playing around with themes, and decided to go with a dark one for my main account
then i decided i wanted a darker firefox theme to match with it all

so i hit up the firefox addons/theme pages and pick a few. 

i think i installed 4, maybe 5. then i hit the "restart firefox" button

then it went to *&%^

firefox not only closed, *everything* on my desktop disappeared, and it logged me out from my account. 

now when i log back in to the main account, gaim flashed briefly on the desktop, then disappears, and *nothing* shows up. oh, except my wallpaper ;)

the only way to get a response is to ctrl+alt+backspace (of course) or alt+f4 brings up the shut-down options. right-clicking the mouse does nothing

so im using a secondary account, but would *love* to hear some ideas on how to get things showing up in the first one properly

any ideas?

---

### Post by shareMenaPeace on 2007-02-04
Try login from LOGIN with 

Session -> Failsafe

Than open a terminal and type

```
killall xfc4-panel
```

or just 

```
xfc4-panel
```

---

### Post by xSauronx on 2007-02-04
> **shareMenaPeace said:**
> Try login from LOGIN with 

Session -> Failsafe

Than open a terminal and type

```
killall xfc4-panel
```

or just 

```
xfc4-panel
```

killall returned "no processes killed"

the xfce4-panel brings up the default xfce4 panel (meh! ;) )
and xfce4-session brings up....well, it starts to load, and then all i can see is the gaim window again. 

but nothing else changes, and "logging out" of that session takes me back to the failsafe terminal

---


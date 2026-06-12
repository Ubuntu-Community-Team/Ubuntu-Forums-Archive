---
title: "Xdotool Usage"
date: 2014-01-01
forum: Any Other OS
---

### Post by MustangGT on 2014-01-01
Hi Guys,

I use xdotool to simulate keypresses from a shell script. 

This normally works just fine.  However, I need to send a key combo which is Ctrl+Alt+H.  I wrote an xdo command for it and it acts weird, as in, out of every 3-4 presses only once it will work.  All other key combos work fine.  Can anyone confirm if maybe I have a syntax error here? 

```
xdotool keydown ctrl keydown Alt_L key h keyup ctrl keyup Alt_L;
```

Just a side note, the reason I want to simultate that key combo is to call the ParcelLite menu.  I want to call it from an auxilary mouse button, I use xbindkeys to call the mouse and xdotool to simultate the keyboard combo.

---


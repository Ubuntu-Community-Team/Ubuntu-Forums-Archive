---
title: "Custom OS X like keybindings for Copy and Paste"
date: 2008-01-18
forum: Apple Intel Users
---

### Post by tehkain on 2008-01-18
I am wondering if its possible to bind Super(Command)-C/V to Copy/Paste? I have already switched my capslock to a control but sadly my thumbs are more effective for this task. I do not want to swap my Control and Super because I use both of them for many other things in emacs and gnome.

If this is not possible are there any glipper like programs that allow custom keybindings for my clipboard?

---

### Post by tehkain on 2008-01-19
I solved this using xmacro. I created a coulple scripts like
```

#! /bin/bash 
# Copy via Control+C
sleep .07 
echo KeyStrPress Control_L KeyStrPress c KeyStrRelease c KeyStrRelease Control_L | xmacroplay "$DISPLAY"

```
and
```

#! /bin/bash 
# Paste via Control+V
sleep .07 
echo KeyStrPress Control_L KeyStrPress v KeyStrRelease v KeyStrRelease Control_L | xmacroplay "$DISPLAY"

```

I used my keyboard shortcut xfce pane and added a link to these scripts.Thanks to the 'Easy remap your number pad' thread.

I have one issue left which I am wondering about, can I detect the focused window's title in a bash script?

---


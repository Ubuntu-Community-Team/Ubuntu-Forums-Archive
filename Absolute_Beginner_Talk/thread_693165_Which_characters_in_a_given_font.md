---
title: "Which characters in a given font?"
date: 2008-02-10
forum: Absolute Beginner Talk
---

### Post by Frogbarf on 2008-02-10
I want to know precisely which characters a given font contains. The obvious place to look is character map, but Ubuntu seems provide default characters for those characters not supported by the font selected.

For example, select the Bengali script and the first font listed in the font selection box (**aakar** on my machine). Keeping the cursor in the font selection box, scroll through the list of fonts using the down-arrow key and watch the character display.

For most fonts the character display stays the same, but a few fonts cause the characters to change form. I suspect those few are the only ones that actually have Bengali characters.

It's as though Ubuntu has some hidden resource with all the Unicode characters (or a good many of them) and when the current font doesn't support them, it falls back on that hidden resource. My guess is that the "hidden resource" is some specific font or fonts that act as defaults.

Unfortunately, this pleasant feature is a mal-feature, because it's impossible to tell if the character display is coming from the font selected or somewhere else.


Going into System > Preferences > Font and messing around doesn't tell me what I want to know; the default character set displayed for each font is good old ASCII.

Any suggestions? Even if it was just a method to make Character Map color which cells are being filled in from whatever default Ubuntu uses, that would suffice.

---

### Post by jan quark on 2008-02-11
try this small application
```

sudo apt-get install gnome-specimen
```

it displays the installed fonts and a preview 

run it in terminal by running

```
gnome-specimen
```

---


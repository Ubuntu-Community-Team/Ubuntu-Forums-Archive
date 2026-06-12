---
title: "Location of border opacity settings"
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by FluffyFear on 2007-11-04
Hello.

Neither in CompizConfig Settings Manager nor in this forum i can`t find where opacity settings of window borders is located :( .

Please help me in my search. Some details on screenshot. I`m using version 7.10 of Ubuntu.

---

### Post by benerivo on 2007-11-04
The only place i know of which can affect the opacity of window borders, is in the 'Emerald Theme Manager' settings. You will probably have to install it, as well as having 'the 'Windows Decorations' option ticked in CompizConfig Settings Manager.

---

### Post by FluffyFear on 2007-11-04
AFAIK compiz in gutsy using not emerald but gtk-window-decorator.

I have try all options that can be specified with it, but there is no effect.

---

### Post by FluffyFear on 2007-11-05
Well, I install emerald instead of gtk-window-decorator. There are much more options to configure.

I think emerald better alternative.

---

### Post by jjmatt on 2008-05-17
I realize it's like a year later but...in case you're still curious.

```
gconf-editor
```

apps -> gwd

edit the metacity active theme opacity. I have mine at .5, which I think is nice.

---


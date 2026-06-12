---
title: "Expanding blue box when opening programs"
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by virgilnilson on 2007-05-27
When I start a program such as Firefox, a hollow blue box expands "laggily" from the icon until it fits my screen, then the program pops up immediately to fill it. After initially starting it, minimizing/maximizing appears very smooth and aesthetic with no lag at all.

Is this a bug or is it normal?

I'm on an AMD64 +3200 with an ATI x850.

---

### Post by Viskovitz on 2007-05-28
It doesn't look very normal; maybe it's something related to your video drivers. Have you configured them correctly? Are you using Beryl/Compiz?

---

### Post by Znupi on 2007-05-28
I think it's normal it does move a bit *laggily* for me, too, but it doesn't look so bad...

---

### Post by virgilnilson on 2007-05-28
This problem was fixed by using

```
gconf-editor
```

then going to apps -> panel -> global -> and unchecking "enable_animations".

As far as I can tell this has not disabled any other eyecandy, and programs now open up much faster.

---

### Post by Apollo64X2_linux on 2007-10-23
Hello, I just had a question about this. I am still having the problem even when following the gconf-editor tip. I was wondering if anyone else has any other things I can try because my computer runs real slow when trying to open this and the blue expanding box is still coming up when I click on programs. Thanks for any help!

---

### Post by Viskovitz on 2007-10-24
That's with Feisty/Gutsy and the best ATI drivers available?

---


---
title: "Postscript question!!"
date: 2007-08-29
forum: Absolute Beginner Talk
---

### Post by benevolent on 2007-08-29
Is there any way that I can copy the text from a postscript file????


from the default gnome viewer I can't...



thx in advance:guitar:

---

### Post by benhall on 2007-08-29
I think it depends on the source- if the ps is from a flat scan the text cannot be copied. If the characters are encoded in the ps (ie it was generated from open office or something similar) then you should be able to select the text. What is the source of the postscript file?

---

### Post by bogolisk on 2007-08-29
> **benevolent said:**
> Is there any way that I can copy the text from a postscript file????


from the default gnome viewer I can't...



thx in advance:guitar:

2 choices:
[LIST=1]
[*] use ps2ascii and open the result in an editor such as gedit.
[*] use ps2pdf and copy the text using a pdf viewer such as acroread.
[/LIST]

Those programs are part of the gs-common package.

---


---
title: "Playing supertux"
date: 2007-12-11
forum: Absolute Beginner Talk
---

### Post by quarkhirad on 2007-12-11
Hi . I installed super tux on my xubunut 7.10 and when i ran it it was very sluggish. I have a 1.73Ghz intel pentium M processor and 1Gb ram and no graphics card.

---

### Post by flamelab on 2007-12-11
Have you enabled Compiz Fusion ? Have you properly installed the drivers for your on board graphics card ?[img]http://www.adslgr.com/forum/images/smilies/hmmm.gif[/img]

---

### Post by kstella on 2007-12-11
You mean Compiz Fusion needs to be enabled for the game to work?

---

### Post by quarkhirad on 2007-12-11
I do not have a graphics card. All i have is the standard intel media accelerator . Thats all and yes compiz is on. I tested it again and this time with system monitor open . I realized that if the game was on my cpu usage was  a 100 % and and dint come below that. I think it is to do with that

---

### Post by meindian523 on 2007-12-11
nopes,he means Compiz should be off so that your entire graphics memory can be dedicated to the game....

---

### Post by flamelab on 2007-12-11
> **meindian523 said:**
> nopes,he means Compiz should be off so that your entire graphics memory can be dedicated to the game....

Yes , that thing :) . The best way to enjoy games is to have an xorg based Session , slower is the one with aiglx enabled and slower than that is a xgl based session . And the last two are much slower if Fusion is enabled .

---

### Post by quarkhirad on 2007-12-18
How do i turn off compiz before playing

---

### Post by meindian523 on 2007-12-18
In terminal:

```
metacity --replace
```

will replace compiz with the Gnome default.... :)

---


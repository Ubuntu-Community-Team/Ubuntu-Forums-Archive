---
title: "[SOLVED] Were are the programs installed by SPM"
date: 2008-04-09
forum: Absolute Beginner Talk
---

### Post by scraghty604 on 2008-04-09
I have installed  few things now, and being new i am kinda confused....sometime they show up in the  menus and sometimes they install and are gone  for ex. i installad conky, went off with out a hitch but then vansished no were to be found i found the exec file under search but it did nothing, theres been a few other programs did the same thing thanxs guys

---

### Post by tangibleorange on 2008-04-09
> **scraghty604 said:**
> I have installed  few things now, and being new i am kinda confused....sometime they show up in the  menus and sometimes they install and are gone  for ex. i installad conky, went off with out a hitch but then vansished no were to be found i found the exec file under search but it did nothing, theres been a few other programs did the same thing thanxs guys

well only certain programs installed by synaptic are designed to appear in your menus - there is nothing wrong. to launch the ones not in the menu, just type their name into your terminal. For example, if I wanted to launch firefox, i would just type:

```
firefox
```

into a terminal.

P.S. Many programs need you to edit a config file before you can run them. I think conky is one of those. you'd do well to look at a site telling you how to write a conky config file.

---

### Post by Crafty Kisses on 2008-04-09
> **scraghty604 said:**
> I have installed  few things now, and being new i am kinda confused....sometime they show up in the  menus and sometimes they install and are gone  for ex. i installad conky, went off with out a hitch but then vansished no were to be found i found the exec file under search but it did nothing, theres been a few other programs did the same thing thanxs guys

You can usually run them from Terminal, or they go in your Applications menu.

---

### Post by SunnyRabbiera on 2008-04-09
the best way to see where synaptic puts your stuff is to open up synaptic and in settings under preferences you can make the package manager display where stuff is stored at.
its the first box on the top.

most of the time applications you install are in usr/bin or usr/lib but it depends.
Like if you have a terminal app it would not have a list in the menu.

---


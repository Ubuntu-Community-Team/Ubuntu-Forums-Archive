---
title: "multiple desktops and virtual terminals?"
date: 2007-04-14
forum: Absolute Beginner Talk
---

### Post by syalam on 2007-04-14
How can I disable the multiple desktops in Ubuntu, 99% of the time I only use 1 desktop so I would like to gain some performance here. I also read that if you disable virtual terminals CTRL+ALT+F1-F7 you gain a lot of performance too. I know F7 is your GUI but what are virtual terminals and why are there 6?

---

### Post by chalex on 2007-04-14
right-click on your multiple desktop chooser and go to Preferences

the virtual terminals, called "ttys" are defined in /etc/inittab, the getty section.  you can comment out tty2-6, but it won't make any performance difference.

---

### Post by louieb on 2007-04-14
> **syalam said:**
> How can I disable the multiple desktops in Ubuntu, 99% of the time I only use 1 desktop 
I'll take the east one. Right click on  a work space icon  in the panel > Preferences > the option is here. Don't know that you will get any performance increase by reducing the # of available workspaces.  I do it just to give the panel some more room for other stuff.

Where did you read that disabling some of the virtual terminals would improve performance? It seems the speed demons and the low powered computer users would be all over that.  I have a couple of P3 400's that I would do that to if it works.

Oh I see *chalex *just answered bot questions.

---


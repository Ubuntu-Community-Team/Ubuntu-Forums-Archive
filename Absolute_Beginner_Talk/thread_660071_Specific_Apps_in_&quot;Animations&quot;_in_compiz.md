---
title: "Specific Apps in &quot;Animations&quot; in compiz"
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by markyb86 on 2008-01-06
I cant figure out how to exclude specific apps from compiz fusion animations effects. Its really an eyesore in photoshop when every click the windows fade in.

---

### Post by cartisdm on 2008-01-06
Preferences > Advanced Desktop Effects > Effects

Under the Effects heading you should be able to see Fading Windows.  Try unchecking that if you haven't already.  Or click on the icon (instead of the checkmark) and it should give you even more options to adjust.  If you don't see the Effects section within the Advanced Desktop Effects trying typing it into the Filter in the upper left corner.

---

### Post by markyb86 on 2008-01-06
I like the effect, i just dont want it to be used in wine apps, but more importantly photoshop

---

### Post by PeterJS on 2008-01-06
Here's the compiz guide to identifying specific windows to write custom rules or exclude windows from rules:
[http://wiki.opencompositing.org/WindowMatching](http://wiki.opencompositing.org/WindowMatching)

---

### Post by markyb86 on 2008-01-06
Thanks for the link PeterJS. I tried alot of identifier options and i still cant get it to work..

---

### Post by erlyrisa on 2008-03-29
you just have to delete the "Unknown" match for animations in

close
and
open

--sadly any program outside of GTK that presents a child process like a menu is considered a new window that is to be "opened and closed" - so you have to get rid of that regex expression wich matches those items.

---


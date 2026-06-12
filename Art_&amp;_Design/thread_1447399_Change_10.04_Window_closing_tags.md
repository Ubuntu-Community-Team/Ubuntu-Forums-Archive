---
title: "Change 10.04 Window closing tags"
date: 2010-04-05
forum: Art &amp; Design
---

### Post by Maarek Stele on 2010-04-05
The new beta moved the X tag to the left side of the Window.  How can I change the window to the original setting?

---

### Post by nilarimogard on 2010-04-05
Simply run this in a terminal:
```
gconftool-2 --type string --set /apps/metacity/general/button_layout "menu:minimize,maximize,close"
```

---

### Post by m.rankovic on 2010-04-05
Or this, if you want "maximize minimize close" 

```
gconftool-2 --type string --set /apps/metacity/general/button_layout "maximize,minimze,close"
```

---

### Post by Maarek Stele on 2010-04-05
OK I did what you said, but the grouping of the buttons are still on the left corner of the Window and not in the right.

[IMG]http://afftnq.blu.livefilestore.com/y1p9whKiz4OWW7h2IKpNiCXeb7b_FO5BucVY2RBpB8u-SKyppg8mArBp90WyOnS2V3znWpSypMYHiIR57eGiwjXNfDAkqVZoMHe/wrong_side.jpg[/IMG]

---


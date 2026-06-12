---
title: "Ubuntu minimize boxes?"
date: 2007-01-15
forum: Absolute Beginner Talk
---

### Post by tdrusk on 2007-01-15
I love Ubuntu, but I hate when it minimizes programs it minimizes with a bunch of little boxes. Is there a way I can just have it minimize without the boxes?

---

### Post by meng on 2007-01-15
You mean the window list at the bottom? If you don't want it, just right click and "Delete Panel". Then there'll be no more windowlist visible. Generally, apps only minimize with one "box" per app.
EDIT: Oh, now I understand what you're saying. I completely misunderstood your question. Fortunately, these other two folks knew what you were talking about.

---

### Post by aysiu on 2007-01-15
Alt-F2 ```
gconf-editor
``` Apps > Metacity > General > Reduced_Resources will get rid of those little boxes.

---

### Post by jpeddicord on 2007-01-15
{edit: d'oh, beat to it!}

There is a setting to change that option, but if you change it, windows will move with outlines instead of the whole window. If that is fine with you, follow these steps:
[LIST=1]
[*]Right-click on Applications, and select Edit Menus
[*]Go to System Tools
[*]Make sure Configuration Editor is checked
[*]Close the menu editor, and go to Applications > System Tools > Configuration Editor
[*]Go to this key folder: /apps/metacity/general
[*]In that list, there is an option labeled 'reduced_resources.' Check it if you want to use it.
[*]Close the editor, and the effect will be applied.
[/LIST]

Jacob

---

### Post by Qrk on 2007-01-15
To turn off all animations (not just the minimizing ones) go to the configuration editor, under Apps->Metacity->General and check reduced_resources

---


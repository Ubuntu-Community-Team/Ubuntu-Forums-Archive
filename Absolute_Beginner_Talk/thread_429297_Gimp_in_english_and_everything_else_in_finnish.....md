---
title: "Gimp in english and everything else in finnish.... is that possible?"
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by encompass on 2007-05-01
I want to have gimp in english but everything else in finnish... is there a way for me to do that?

---

### Post by rubinstein on 2007-05-01
Open a terminal and type:
export LANG=en_EN

and then open Gimp with this terminal:
gimp

You could make a script like this:

#!/bin/bash
export LANG=en_EN
gimp

Save it as a text file, make it executable and link it with a gimp icon in your panel.

---

### Post by mahiyar on 2007-05-01
Oh! The beauty of Linux

---

### Post by encompass on 2007-05-01
Cool beans... thanks!  Now because I used the export doesn't that carry to others... or only in that bash...?

---


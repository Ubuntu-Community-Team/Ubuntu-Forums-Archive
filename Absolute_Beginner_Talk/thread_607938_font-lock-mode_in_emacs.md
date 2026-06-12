---
title: "font-lock-mode in emacs"
date: 2007-11-09
forum: Absolute Beginner Talk
---

### Post by spearfish on 2007-11-09
Hey, I'm wondering if there is some emacs guru out there who can help me.  Every time I start emacs, the default is black & white.  I have to type  ALT-X font-lock-mode in order to see the pretty colors.

Does anyone know how to make emacs start up in color all the time?  I'm getting tired of typing ALT-X font-lock-mode every time I run the program.  :KS

thanks!

---

### Post by psusi on 2007-11-09
Enter customize mode and set global-font-lock-mode to t, or edit your ~/.emacs file and add:

(global-font-lock-mode)

---


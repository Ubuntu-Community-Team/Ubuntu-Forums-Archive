---
title: "sudo'ing programs"
date: 2006-07-12
forum: Absolute Beginner Talk
---

### Post by da1nonlymikeo on 2006-07-12
when i start firefox or gaim or any program via sudo in terminal, example "sudo firefox" it comes up stock, no bookmarks, not my homepage, and for gaim theres no screen names. is there a way to make these progams run normaly with all my stuff when i run them from terminal??

---

### Post by ProjectGod on 2006-07-12
try gksudo

let me know how you go. i'm on a windows machine so can't test it myself. a question. why do you use the terminal to open up web browser when you can use the gui?

---

### Post by aysiu on 2006-07-12
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

By the way, if you want to run Firefox normally, just type ```
firefox
``` Forget the *sudo*. You can also (rather than running it from the terminal) press Alt-F2 and type ```
firefox
```

---

### Post by scxtt on 2006-07-12
why are you trying to do that anyway? -- of course it's not gonna use your configs when you run it by prefacing it by sudo (i.e. as 'root') ...

---

### Post by da1nonlymikeo on 2006-07-12
okay so gksudo dident work, but just typing firefox, or gaim works well. the reason why i ask is because i hate desktop items and toolbar icons lol.

---

### Post by aysiu on 2006-07-12
You may be interested in this, then:
[http://doc.gwos.org/index.php/GnomeKeyboardShortcut](http://doc.gwos.org/index.php/GnomeKeyboardShortcut)

---

### Post by scxtt on 2006-07-12
you could also add a "run program" applet to gnome, if you use gnome -- tho i'm sure KDE has something similar ...

---


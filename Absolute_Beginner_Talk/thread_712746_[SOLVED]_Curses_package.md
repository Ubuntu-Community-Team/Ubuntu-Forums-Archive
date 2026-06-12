---
title: "[SOLVED] Curses package"
date: 2008-03-02
forum: Absolute Beginner Talk
---

### Post by Faud on 2008-03-02
[/code]
checking for initscr in -lcurses... no
checking for initscr in -lncurses... no
checking for initscr in -lpdcurses... no
configure: error: A curses library is required to use the debugger
[/code]
I tried to install libcurses but that did not work. any ideas ?

---

### Post by kellemes on 2008-03-02
Curses-library, isn't this provided by ncurses?
Do you have ncurses-bin installed?

---

### Post by jan quark on 2008-03-02
perhaps you need the development package of libcurses

install this
```

sudo apt-get install libncurses5-dev libncursesw5-dev libncursesw5 libncurses5
```

---

### Post by Faud on 2008-03-02
Thanks guys, Marked as solved.

---

### Post by gajanan.khandake on 2008-03-19
Thank's jan quark.
It solved my problem too.
:guitar:

---


---
title: "Running GTK in terminal??"
date: 2007-01-12
forum: Absolute Beginner Talk
---

### Post by shadowphoenix on 2007-01-12
Hi there,
          I am having some problem running a program call ettercap in the terminal it says that GTK support not compiled in ettercap.What should i do in order for me to run this program in terminal.

---

### Post by sardion on 2007-01-12
Either you need to instead install the ettercap-gtk package (which has GTK support) or run the command as:

ettercap -T

which tells it text mode.  I found that info by googling and I expect it would be on the ettercap man page as well.  When in doubt about running a command some way or other, always try

man ettercap

man <CMD>

etc.

Hope this helps.

---


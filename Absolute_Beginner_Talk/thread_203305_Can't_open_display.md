---
title: "Can't open display:"
date: 2006-06-25
forum: Absolute Beginner Talk
---

### Post by soumya on 2006-06-25
hiii
i have installed ubuntu newly.. i hav the current version of postgresql installed also.
i was tryin to look at the codes using ddd. however whenever i invoke ddd by the ddd   & command the following output is shown.
=================================================

postgres@rintu:~/ddd/ddd-3.3.12-test2$ ddd &
[1] 8722
postgres@rintu:~/ddd/ddd-3.3.12-test2$ Error: Can't open display: 

[1]+  Exit 1                  ddd
================================================
i tried to export the DISPLAY variable also but the problem was not corrected n the same output showed when tryin t invoke ddd.

================================================
postgres@rintu:~/ddd/ddd-3.3.12-test2$ export DISPLAY=localhost:0.0
postgres@rintu:~/ddd/ddd-3.3.12-test2$ ddd &
[1] 8722
postgres@rintu:~/ddd/ddd-3.3.12-test2$ Error: Can't open display: localhost:0.0

[1]+  Exit 1                  ddd

================================================

can anyone find me the solution to this problem?

---

### Post by hippy4life on 2006-06-25
are you running this command from a tty terminal or from and xterm ?

---

### Post by soumya on 2006-06-25
>are you running this command from a tty terminal or from and xterm ?

i am runnin this command from xterm.

---


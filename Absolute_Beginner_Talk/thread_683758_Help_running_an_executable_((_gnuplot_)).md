---
title: "Help running an executable (( gnuplot ))"
date: 2008-01-31
forum: Absolute Beginner Talk
---

### Post by Xtrmi on 2008-01-31
Hi I installed gnuplot yesterday  and the icon never showed up in any of the menus so i browsed to it and tried to execute it and notin happend. I can go into the consol and type sudo gnuplot but all i get is some info on the program. How do I get this program to open in a window. Also how would I get its icon in the applications menu? Thanks for any help u can provide.

---

### Post by jrothwell97 on 2008-01-31
Gnuplot is a command-line application, therefore it has no 'window' as such. You could try typing 'sudo gnuplot --help' or 'sudo man gnuplot' to ask for help on how to work it at the command line.

---

### Post by emarkd on 2008-01-31
You shouldn't have to run it with sudo.  Always avoid doing anything as sudo unless you have to.  What happens when you just run 'gnuplot'?

You can add something to your menu by right-clicking on the menus and selecting "Edit Menus"

---

### Post by jan quark on 2008-01-31
> A command-line driven interactive plotting program

taken from the description in the synaptic package manager
it seems that application is only executable  in  text mode

---

### Post by seventhc on 2008-01-31
You might want to have a look at this [http://www.gnuplot.info/faq/](http://www.gnuplot.info/faq/)

---


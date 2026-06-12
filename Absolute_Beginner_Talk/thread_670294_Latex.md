---
title: "Latex"
date: 2008-01-17
forum: Absolute Beginner Talk
---

### Post by bipul on 2008-01-17
[B]I have gedit
And i heard that one can do the latex jobs on gedit.

How to go about it....... anyone may help please...!:)[/B]

---

### Post by Borbus on 2008-01-17
Well LaTeX is a markup language which you can do in a text editor and then compile it later with your choice of LaTeX distribution and program (ie. pdflatex). There is a plugin for gedit which is included called "External Tools" which you can use to make it easy to compile something from within gedit, ie. I think you would do pdflatex $GEDIT_CURRENT_DOCUMENT... you might have to look that up, though, it's probably wrong.

edit: Actually, check this out, I think it is exactly what you want: [http://live.gnome.org/Gedit/LaTeXPlugin](http://live.gnome.org/Gedit/LaTeXPlugin)

---

### Post by bipul on 2008-01-17
Oh thanks Borbos for calling in.

well i was recently hearing from friends that one can do the Latex compilings from gedit... i had no clue.

Infact I  downloaded a package called tex maker... but the problem is what ever i do i get the message  log files cannot be found so... stopped blah blah.

Can u provide a better insight now.
I need to start lateing very soon but u see

---

### Post by bipul on 2008-01-17
Can u suggest any other package that u think is better...


ooopsi i have a power cut got to go!

---

### Post by mali2297 on 2008-01-17
Install the package [texlive-latex-recommended]("http://packages.ubuntu.com/feisty/tex/texlive-latex-recommended") with all of its dependencies. Use Synaptic.

If you cannot compile from GEdit, try
```

pdflatex yourfile.tex

```
from the terminal.

---

### Post by Whiffle on 2008-01-17
Do yourself a favor, even if you're a gnome user, and install Kile.  Its a very very handy LaTeX environment.  If you don't like it, you can always remove it.

---

### Post by bipul on 2008-01-18
Thanks mail 2297 & whiffie.

I'll try what u said & inform about what i faced ...   i f that did not work.

---

### Post by Borbus on 2008-01-18
I actually prefer the gedit latex plugin but Kile is still very nice. I installed tetex first (apt-get install tetex-core tetex-bin tetex-extra), then after you install gedit you need to edit the commands for compiling because it has rubber commands by default. Change the PDF one to pdflatex %f, that's it, now you can just press the PDF button to get a PDF. I only use pdflatex so I don't know exactly what to do for the others.

---


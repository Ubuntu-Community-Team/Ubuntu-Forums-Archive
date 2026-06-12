---
title: "Need help using TeTex"
date: 2008-01-30
forum: Absolute Beginner Talk
---

### Post by spearfish on 2008-01-30
I used the Synaptic package manager to install TeTex, because I need to use BibTex for school.

My problem is that I can't seem to find and start the TeTex application.  A whole bunch of TeTex related files are now installed in the /usr/share  folder, and also the /var/lib/dpkg/info folder.  However, nothing there looks like an executable.

How do I start the TeTex application?

Thanks

---

### Post by scizzo on 2008-01-30
Well isnt the tex applications there for converting the file/files you create to pdf or ps format then you can use either ghostscript or the like to view the pdf and ps file afterwards?

---

### Post by spearfish on 2008-01-30
> **scizzo said:**
> Well isnt the tex applications there for converting the file/files you create to pdf or ps format then you can use either ghostscript or the like to view the pdf and ps file afterwards?

Sorry... I didn't understand that at all.

---

### Post by lsmobrian on 2008-01-30
install winefish for writing latex if you need a gui

install jabref for bibtex



if your compiling a latex paper with bibtex. you will have a .tex file and a .bib file

to compile it in command line for ex. paper named forums.tex and and forums.bib

latex forums.bib   (compiles paper)
latex forums         (makes pointers for bib references)
bibtex forums.bib (makes database for references)
latex forums         (adds references to paper)


I'm pretty sure thats the commands, but i dont have it installed right now, this is just from memory

i only used the gui's for writing, and always compiled this way, im sure there is a way to do it gui, just never have

---


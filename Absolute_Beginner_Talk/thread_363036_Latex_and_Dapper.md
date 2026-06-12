---
title: "Latex and Dapper"
date: 2007-02-16
forum: Absolute Beginner Talk
---

### Post by sabrina on 2007-02-16
Does anyone know where to get fixme.sty?

When I run pdflatex on a file it says:

LaTeX2e <2003/12/01>
Babel <v3.8d> and hyphenation patterns for american, french, german, ngerman, b
ahasa, basque, bulgarian, catalan, croatian, czech, danish, dutch, esperanto, e
stonian, finnish, greek, icelandic, irish, italian, latin, magyar, norsk, polis
h, portuges, romanian, russian, serbian, slovak, slovene, spanish, swedish, tur
kish, ukrainian, nohyphenation, loaded.
\@input{preamble-rapport.aux}
(./preamble-rapport.tex

! LaTeX Error: \usepackage before \documentclass.

See the LaTeX manual or LaTeX Companion for explanation.
Type H <return> for immediate help.
...

l.19 \usepackage{
t1enc}
? ! Interruption.
\GenericError ...
\endgroup
l.19 \usepackage{
t1enc}
?


I've install tetex-base, tetex-bin and tetex-extra (plus all the recommended packages that the command 'sudo aptitude install tetex-...' lists.

Regards Sabrina

---

### Post by dada1958 on 2007-02-17
[http://www.tug.org/texlive/devsrc/Master/texmf-dist/tex/latex/fixme/fixme.sty](http://www.tug.org/texlive/devsrc/Master/texmf-dist/tex/latex/fixme/fixme.sty)

I recommend the TexLive 2005 install because development of teTeX is discontinued ...

[http://www.tug.org/texlive/](http://www.tug.org/texlive/)

---

### Post by sabrina on 2007-02-17
Hi!

I've installed texlive, but it still says that the packages are missing?

Thanks for the answer!

---


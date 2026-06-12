---
title: "Texlive - missing packages"
date: 2007-02-17
forum: Absolute Beginner Talk
---

### Post by sabrina on 2007-02-17
hi!

I've installed Texlive on Edgy, but when I type "pdflatex file.tex" it says:

l.19 \usepackage{
                 t1enc}
? 

! LaTeX Error: \usepackage before \documentclass.

See the LaTeX manual or LaTeX Companion for explanation.
Type  H <return>  for immediate help.
 ...                                              
                                                  
l.20 \usepackage[danish]{
                         babel} % support for bl.a dansk orddeling, i miktex...


And it continues to say that the packages are missing. What can I do?

---

### Post by silentb on 2007-02-20
\documentclass[fleqn]{article}
\usepackage[utf8]{inputenc}
\usepackage[T1]{fontenc}
...

\begin{document}
...
\end{document}

---


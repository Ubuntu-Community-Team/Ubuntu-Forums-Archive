---
title: "Latex errors"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by elexhobby on 2007-04-22
Hi..
I am a newbie to the world of Latex and was learning it through tutorials at [http://www.andy-roberts.net/misc/latex/index.html](http://www.andy-roberts.net/misc/latex/index.html)

The first document Hello World worked fine. However the second document gives me the following error

latex first.tex
This is pdfeTeX, Version 3.141592-1.21a-2.2 (Web2C 7.5.4)
entering extended mode
(./first.tex
LaTeX2e <2003/12/01>
Babel <v3.8d> and hyphenation patterns for american, french, german, ngerman, b
ahasa, basque, bulgarian, catalan, croatian, czech, danish, dutch, esperanto, e
stonian, finnish, greek, icelandic, irish, italian, latin, magyar, norsk, polis
h, portuges, romanian, russian, serbian, slovak, slovene, spanish, swedish, tur
kish, ukrainian, nohyphenation, loaded.
(/usr/share/texmf-tetex/tex/latex/base/article.cls
Document Class: article 2004/02/16 v1.4f Standard LaTeX document class
(/usr/share/texmf-tetex/tex/latex/base/size10.clo))
(/usr/share/texmf-tetex/tex/latex/psnfss/times.sty) (./first.aux)
(/usr/share/texmf-tetex/tex/latex/psnfss/ot1ptm.fd)
! Undefined control sequence.
\@title ->How to Structure a \Latex
                                    {} Document
l.13 \maketitle

?


What could be the error? My first.tex file is as under - 

\documentclass{article}
\usepackage{times}

\begin{document}

\title{How to Structure a \Latex{} Document}
\author{Andrew Roberts\\
			School of Computing,\\
			University of Leeds,\\
			United Kingdom\\
			\texttt{andyr@comp.leeds.ac.uk}}
\date{\today}
\maketitle
\end{document}

I have installed tetex-bin, tetex-base, and tetex-extra..
Please help..

---

### Post by tkjacobsen on 2007-04-22
\title{How to Structure a \Latex{} Document}
\author{Andrew Roberts\\
School of Computing,\\
University of Leeds,\\
United Kingdom\\
\texttt{andyr@comp.leeds.ac.uk}}
\date{\today}

should be before \begin{document}

---

### Post by elexhobby on 2007-04-22
No its after \begin{document} in the tutorial too.. Anyways I tried it and got the following error: -


latex first.tex
This is pdfeTeX, Version 3.141592-1.21a-2.2 (Web2C 7.5.4)
entering extended mode
(./first.tex
LaTeX2e <2003/12/01>
Babel <v3.8d> and hyphenation patterns for american, french, german, ngerman, b
ahasa, basque, bulgarian, catalan, croatian, czech, danish, dutch, esperanto, e
stonian, finnish, greek, icelandic, irish, italian, latin, magyar, norsk, polis
h, portuges, romanian, russian, serbian, slovak, slovene, spanish, swedish, tur
kish, ukrainian, nohyphenation, loaded.
(/usr/share/texmf-tetex/tex/latex/base/article.cls
Document Class: article 2004/02/16 v1.4f Standard LaTeX document class
(/usr/share/texmf-tetex/tex/latex/base/size10.clo))
(/usr/share/texmf-tetex/tex/latex/psnfss/times.sty)

! LaTeX Error: Missing \begin{document}.

See the LaTeX manual or LaTeX Companion for explanation.
Type  H <return>  for immediate help.
 ...

l.10 \maketitle

?

---

### Post by tkjacobsen on 2007-04-22
I always have it before \begin{document}, and that is working. Maybe it can be both.

This is working
```


\documentclass{article}
\usepackage{times}

\begin{document}
\title{How to Structure a \LaTeX Document}
\author{Andrew Roberts\\
School of Computing,\\
University of Leeds,\\
United Kingdom\\
\texttt{andyr@comp.leeds.ac.uk}}
\date{\today}
\maketitle
\end{document}
```

You just mistyped \LaTeX

---

### Post by elexhobby on 2007-04-22
Thanks.. Sorry for the silly error.. Now it doesn't output any errors but the dvi file created is not normal.. I mean the icon has a orange watch symbol on it.. Normally it should disappear after a few seconds, but its permanent here...  Also when I tried opening the dvi file through evince, it just keeps on showing 'Loading".. I tried dvipdf and it gives me the following error - 

dvipdf first.tex first.pdf
dvips: ! Bad DVI file: first byte not preamble

The first.pdf is created, but again, it doesn't open using evince..

This is the output that I'd got when I created the dvi file, just in case it helps - 

latex first.tex
This is pdfeTeX, Version 3.141592-1.21a-2.2 (Web2C 7.5.4)
entering extended mode
(./first.tex
LaTeX2e <2003/12/01>
Babel <v3.8d> and hyphenation patterns for american, french, german, ngerman, b
ahasa, basque, bulgarian, catalan, croatian, czech, danish, dutch, esperanto, e
stonian, finnish, greek, icelandic, irish, italian, latin, magyar, norsk, polis
h, portuges, romanian, russian, serbian, slovak, slovene, spanish, swedish, tur
kish, ukrainian, nohyphenation, loaded.
(/usr/share/texmf-tetex/tex/latex/base/article.cls
Document Class: article 2004/02/16 v1.4f Standard LaTeX document class
(/usr/share/texmf-tetex/tex/latex/base/size10.clo))
(/usr/share/texmf-tetex/tex/latex/psnfss/times.sty) (./first.aux)
(/usr/share/texmf-tetex/tex/latex/psnfss/ot1ptm.fd)
(/usr/share/texmf-tetex/tex/latex/psnfss/ot1pcr.fd) [1] (./first.aux) )
Output written on first.dvi (1 page, 624 bytes).
Transcript written on first.log.

---

### Post by tkjacobsen on 2007-04-22
dvipdf only uses the pdf...
dvipdf first.pdf

By the way, if you want pdf's you can just use pdflatex:
pdflatex first.tex

---

### Post by engla on 2007-04-22
Use pdflatex right from the beginning! 
'pdflatex file.tex'


Added: If you need more latex tools, there is a [Latex plugin for gedit]("http://live.gnome.org/Gedit/Plugins") (gnome text editor) if you use that.

---

### Post by elexhobby on 2007-04-22
Oh.. Its some problem with evince then.. I installed xpdf and it opens the files correctly.. I wonder how suddenly all my pdf file icons have the orange clock on them and none of them open using evince.. All of them work fine with xpdf though.. I even upgraded evince through Synaptic, but no use.. What is gone wrong with evince? I find it much better than xpdf..

---


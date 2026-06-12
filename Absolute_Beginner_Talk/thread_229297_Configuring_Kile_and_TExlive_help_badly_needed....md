---
title: "Configuring Kile and TExlive: help badly needed..."
date: 2006-08-04
forum: Absolute Beginner Talk
---

### Post by krugman on 2006-08-04
Hello!

I have now decided that it was time to install Ubuntu on my main computer, but I still have a big problem with my most important app, namely a Tex writer, ie, Kile.

Following some advice, I decided to use it, but I still can't compile, although I don't have any critical failures when I do the system check. But, pdflatex (which is the thing I need) is not working properly. He finds the binary, but it tells me that it is not properly configured.
Here are the results of the check:

```
#script:/bin/sh
#basedir:/tmp/kde-fred/kileF5C3pe/

[TeX]
mustpass=where,basic,kile
executable=tex
where=/usr/bin/tex
version=3.141592
basic=0
kile=0

[PDFTeX]
mustpass=
executable=pdftex
where=/usr/bin/pdftex
basic=0
kile=0

[LaTeX]
mustpass=where,basic,kile
executable=latex
where=/usr/bin/latex
basic=0
kile=0
src=0
srcpkg=1

[PDFLaTeX]
mustpass=
executable=pdflatex
where=/usr/bin/pdflatex
basic=0
kile=1

[DVItoPS]
mustpass=
executable=dvips
where=/usr/bin/dvips
kile=0

[DVItoPDF]
mustpass=
executable=dvipdfm
where=/usr/bin/dvipdfm
kile=0

[PStoPDF]
mustpass=
executable=ps2pdf
where=/usr/bin/ps2pdf
kile=0

[BibTeX]
mustpass=
executable=bibtex
where=/usr/bin/bibtex
basic=2

[MakeIndex]
mustpass=
executable=makeindex
where=/usr/bin/makeindex
basic=0
kile=0

[KDVI]
mustpass=where
executable=kdvi
where=/usr/bin/kdvi

[KGhostView]
mustpass=
executable=kghostview
where=

[KPDF]
mustpass=
executable=kpdf
where=

[Gv]
mustpass=
executable=gv
where=

[Acroread]
mustpass=
executable=acroread
where=/usr/bin/acroread

```

Basically, when I tell him to compile, he exits with status 1 (what's that?) and when I tell him to view PDF, he says that there is no pdf file to watch...
In the advanced tab of PDFLATEX in Settings I use "Modern" then "run outside kile" and "LATEX" as the class...

Any idea why it does not work?
Thanks for the help, I am becoming desperate now:(

---


---
title: "Encoding error in Kile or do I miss something?"
date: 2007-09-01
forum: Absolute Beginner Talk
---

### Post by QuITh on 2007-09-01
I create a file in kile (Set encoding UTF-eight),
> \documentclass[a4paper,10pt]{report}

\usepackage[utf8]{inputenc}
\usepackage[[COLOR="Lime"]ngerman[/COLOR]]{babel}
\usepackage[T1]{fontenc}
\usepackage[dvips]{graphicx}
\usepackage{color}
\usepackage{url}

\author{Patrick Hoo}
\title{Ubuntu GNU\^{}Linux}
\date{\today}


\begin{document}
\maketitle

\begin{abstract}
I am writing this report for fun, I defined it as ``My own Patrickism Ubuntu GNU\^{}Linux''. If you ask, what does the word ``Patrickism'' mean? The shortest answer is that, I really don't know.

My name is Patrick Hoo, with the Chinese name Gengfeng Hu. I am a cynical boy, physics enthuisiat, \TeX{}Live user, Google fan, and absoultely Ubuntu lover.
\end{abstract}

\tableofcontents

\chapter{Installation of the OS}

\chapter{Using \TeX{}Live \& \TeX{}maker}

\chapter{List of the installed packages}

\chapter{Tips\&HowTos of routine work}

\chapter{Notable open source softwares}


\end{document}
then run "Quick Build" TWICE, LaTeX+ViewDVI as default.
Here is the Log & Messages
> [LaTeX] ubuntu.tex => ubuntu.dvi (latex)
[LaTeX] 0 errors, 0 warnings, 0 badboxes
[LaTeX] Done!

[ViewDVI] ubuntu.dvi (kdvi)
[ViewDVI] Done!
Here is the Output
> *****
*****     LaTeX output: 
*****     cd '/home/v/Patrick'
*****     latex -interaction=nonstopmode 'ubuntu.tex'
*****
This is pdfeTeX, Version 3.141592-1.21a-2.2 (Web2C 7.5.4)
entering extended mode
(./ubuntu.tex
LaTeX2e <2003/12/01>
Babel <v3.8d> and hyphenation patterns for american, french, german, ngerman, b
ahasa, basque, bulgarian, catalan, croatian, czech, danish, dutch, esperanto, e
stonian, finnish, greek, icelandic, irish, italian, latin, magyar, norsk, polis
h, portuges, romanian, russian, serbian, slovak, slovene, spanish, swedish, tur
kish, ukrainian, nohyphenation, loaded.
(/usr/share/texmf-tetex/tex/latex/base/report.cls
Document Class: report 2004/02/16 v1.4f Standard LaTeX document class
(/usr/share/texmf-tetex/tex/latex/base/size10.clo))
(/usr/share/texmf-tetex/tex/latex/base/inputenc.sty
(/usr/share/texmf-tetex/tex/latex/base/utf8.def
(/usr/share/texmf-tetex/tex/latex/base/t1enc.dfu)
(/usr/share/texmf-tetex/tex/latex/base/ot1enc.dfu)
(/usr/share/texmf-tetex/tex/latex/base/omsenc.dfu)))
(/usr/share/texmf-tetex/tex/generic/babel/babel.sty
(/usr/share/texmf-tetex/tex/generic/babel/ngermanb.ldf
(/usr/share/texmf-tetex/tex/generic/babel/babel.def)))
(/usr/share/texmf-tetex/tex/latex/base/fontenc.sty
(/usr/share/texmf-tetex/tex/latex/base/t1enc.def))
(/usr/share/texmf-tetex/tex/latex/graphics/graphicx.sty
(/usr/share/texmf-tetex/tex/latex/graphics/keyval.sty)
(/usr/share/texmf-tetex/tex/latex/graphics/graphics.sty
(/usr/share/texmf-tetex/tex/latex/graphics/trig.sty)
(/usr/share/texmf-tetex/tex/latex/graphics/graphics.cfg)
(/usr/share/texmf-tetex/tex/latex/graphics/dvips.def)))
(/usr/share/texmf-tetex/tex/latex/graphics/color.sty
(/usr/share/texmf-tetex/tex/latex/graphics/color.cfg)
(/usr/share/texmf-tetex/tex/latex/graphics/dvipsnam.def))
(/usr/share/texmf-tetex/tex/latex/url/url.sty)
No file ubuntu.aux.
[1] [1]
No file ubuntu.toc.
[1]
Kapitel 1.
[2]
Kapitel 2.
[3]
Kapitel 3.
[4]
Kapitel 4.
[5]
Kapitel 5.
[6] (./ubuntu.aux) )
Output written on ubuntu.dvi (8 pages, 3092 bytes).
Transcript written on ubuntu.log.
*****
*****     ViewDVI output: 
*****     cd '/home/v/Patrick'
*****     kdvi 'ubuntu.dvi'
*****
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
QApplication::notify: Unexpected null receiver
*****
*****     LaTeX output: 
*****     cd '/home/v/Patrick'
*****     latex -interaction=nonstopmode 'ubuntu.tex'
*****
This is pdfeTeX, Version 3.141592-1.21a-2.2 (Web2C 7.5.4)
entering extended mode
(./ubuntu.tex
LaTeX2e <2003/12/01>
Babel <v3.8d> and hyphenation patterns for american, french, german, ngerman, b
ahasa, basque, bulgarian, catalan, croatian, czech, danish, dutch, esperanto, e
stonian, finnish, greek, icelandic, irish, italian, latin, magyar, norsk, polis
h, portuges, romanian, russian, serbian, slovak, slovene, spanish, swedish, tur
kish, ukrainian, nohyphenation, loaded.
(/usr/share/texmf-tetex/tex/latex/base/report.cls
Document Class: report 2004/02/16 v1.4f Standard LaTeX document class
(/usr/share/texmf-tetex/tex/latex/base/size10.clo))
(/usr/share/texmf-tetex/tex/latex/base/inputenc.sty
(/usr/share/texmf-tetex/tex/latex/base/utf8.def
(/usr/share/texmf-tetex/tex/latex/base/t1enc.dfu)
(/usr/share/texmf-tetex/tex/latex/base/ot1enc.dfu)
(/usr/share/texmf-tetex/tex/latex/base/omsenc.dfu)))
(/usr/share/texmf-tetex/tex/generic/babel/babel.sty
(/usr/share/texmf-tetex/tex/generic/babel/ngermanb.ldf
(/usr/share/texmf-tetex/tex/generic/babel/babel.def)))
(/usr/share/texmf-tetex/tex/latex/base/fontenc.sty
(/usr/share/texmf-tetex/tex/latex/base/t1enc.def))
(/usr/share/texmf-tetex/tex/latex/graphics/graphicx.sty
(/usr/share/texmf-tetex/tex/latex/graphics/keyval.sty)
(/usr/share/texmf-tetex/tex/latex/graphics/graphics.sty
(/usr/share/texmf-tetex/tex/latex/graphics/trig.sty)
(/usr/share/texmf-tetex/tex/latex/graphics/graphics.cfg)
(/usr/share/texmf-tetex/tex/latex/graphics/dvips.def)))
(/usr/share/texmf-tetex/tex/latex/graphics/color.sty
(/usr/share/texmf-tetex/tex/latex/graphics/color.cfg)
(/usr/share/texmf-tetex/tex/latex/graphics/dvipsnam.def))
(/usr/share/texmf-tetex/tex/latex/url/url.sty) (./ubuntu.aux) [1] [1]
(./ubuntu.toc) [1]
Kapitel 1.
[2]
Kapitel 2.
[3]
Kapitel 3.
[4]
Kapitel 4.
[5]
Kapitel 5.
[6] (./ubuntu.aux) )
Output written on ubuntu.dvi (8 pages, 3412 bytes).
Transcript written on ubuntu.log.
*****
*****     ViewDVI output: 
*****     cd '/home/v/Patrick'
*****     kdvi 'ubuntu.dvi'
*****
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
QApplication::notify: Unexpected null receiver
But in the output dvi file, the "abstract" is "Zusammenfassung", the "Contents" is "Inhaltsverzeichnis", and the "Chapter" is "Kapitel". 

Could you tell me why? Thanks in advance.

---

### Post by QuITh on 2007-09-01
BTW, I installed
> kdvi, kile, konsole, kviewshell, tetex-base, tetex-bin, tetex-doc, tetex-extra, tex-common, texinfo, texmaker
under my Ubuntu GNU/Linux 7.04

---

### Post by Chris S. on 2007-09-01
Is the problem the german translation?  For instance, should "chapter" not be "kapitel?"  What is \usepackage[ngerman]{babel} supposed to do?

---

### Post by QuITh on 2007-09-01
Oh thanks for you help, Chris S.
I am a native Chinese Simplified speaker, and I just know little about English and Japanese.

> \usepackage[[COLOR="Magenta"]english[/COLOR]]{babel}

---

### Post by Chris S. on 2007-09-01
Oh, good.  I was actually typing up a much longer response giving a detailed solution to what you've already found.

The basic idea of it was that if you use the babel package to include different languages, then you can use the \selectlanguage command to switch between them.  That way you can still get typesetting for other languages but still have headers and other things in the language of your choice.

But it's good that it's settled :)

---

### Post by QuITh on 2007-09-01
Well, maybe I will use Chinese Simplified and English together. :)
Watching the doc file now. Thanks again.

---


---
title: "latex/dvi/texmaker/kile"
date: 2006-12-28
forum: Absolute Beginner Talk
---

### Post by findik1 on 2006-12-28
Hi,
I used latex via texmaker and kile also from terminal. They all did not produce dvi. therefore dvips, dvipdf doesnot work in Texmaker and Kile. I assume it is related to latex (not texmaker or kile). pdflatex (in Texmaker) works fine so I can get pdf automatically but without success of eps figures. 

Any idea what's the problem?

thanks,
findik

---

### Post by NoNo_231 on 2006-12-28
You could try from a terminal "latex name_of_file.tex" to see what is the error. Probaly a package or a missing or mispelled figure, anyway it will show.

However if you want the pdf and not the dvi, you could change the the eps to other file format like png or jpg or even pdf and use them using the graphicx package.

\usepackage{graphicx}

Be sure to have installed the extra packages you need.

---

### Post by rasputin1575 on 2006-12-28
Following from the previous post, once u latex the file frm terminal, i.e latex *** , just do xdvi *** and see what happens. and then dvips ***.
I'd love to read what you get , so pls reply.

---

### Post by findik1 on 2006-12-28
thanks for the quick reply. I must add previously I was using windows, MikTeX with winedt and there is no mistake with it. when I run latex on texmaker/kile I get: process started, process exited normally. On terminal as you asked I get following:
This is pdfeTeX, Version 3.141592-1.21a-2.2 (Web2C 7.5.4)
entering extended mode
(./test.tex
LaTeX2e <2003/12/01>
Babel <v3.8d> and hyphenation patterns for american, french, german, ngerman, b
ahasa, basque, bulgarian, catalan, croatian, czech, danish, dutch, esperanto, e
stonian, finnish, greek, icelandic, irish, italian, latin, magyar, norsk, polis
h, portuges, romanian, russian, serbian, slovak, slovene, spanish, swedish, tur
kish, ukrainian, nohyphenation, loaded.
(/usr/share/texmf-tetex/tex/latex/base/article.cls
Document Class: article 2004/02/16 v1.4f Standard LaTeX document class
(/usr/share/texmf-tetex/tex/latex/base/size11.clo)) (./osajnl.sty
(/usr/share/texmf-tetex/tex/latex/cite/overcite.sty)
(/usr/share/texmf-tetex/tex/latex/cite/cite.sty)
(/usr/share/texmf-tetex/tex/latex/geometry/geometry.sty
(/usr/share/texmf-tetex/tex/latex/graphics/keyval.sty)
(/usr/share/texmf-tetex/tex/latex/geometry/geometry.cfg))
(/usr/share/texmf-tetex/tex/latex/graphics/color.sty
(/usr/share/texmf-tetex/tex/latex/graphics/color.cfg)
(/usr/share/texmf-tetex/tex/latex/graphics/dvips.def)
(/usr/share/texmf-tetex/tex/latex/graphics/dvipsnam.def))
(/usr/share/texmf-tetex/tex/latex/graphics/graphicx.sty
(/usr/share/texmf-tetex/tex/latex/graphics/graphics.sty
(/usr/share/texmf-tetex/tex/latex/graphics/trig.sty)
(/usr/share/texmf-tetex/tex/latex/graphics/graphics.cfg)
(/usr/share/texmf-tetex/tex/latex/graphics/pdftex.def))))
(/usr/share/texmf-tetex/tex/latex/subfigure/subfigure.sty
****************************************
* Local config file subfigure.cfg used *
****************************************
(/usr/share/texmf-tetex/tex/latex/subfigure/subfigure.cfg))
(/usr/share/texmf-tetex/tex/latex/setspace/setspace.sty
Package: `setspace' 6.7 <2000/12/01>
) (/usr/share/texmf-tetex/tex/latex/tools/bm.sty)
(/usr/share/texmf-tetex/tex/latex/preprint/fullpage.sty) (./test.aux)
(/usr/share/texmf-tetex/tex/context/base/supp-pdf.tex
(/usr/share/texmf-tetex/tex/context/base/supp-mis.tex
loading : Context Support Macros / Miscellaneous (2004.10.26)
)
loading : Context Support Macros / PDF (2004.03.26)
) [1{/var/lib/texmf/fonts/map/pdftex/updmap/pdftex.map}]
</home/matlabuser/papers/spie07/epspdt/polyex.eps>
</home/matlabuser/papers/spie07/epspdt/polyemission.eps> [2
Non-PDF special ignored!
Non-PDF special ignored!] <./epspdt/ICG_SET.eps> <./epspdt/SETtau.eps>

LaTeX Warning: `h' float specifier changed to `ht'.

[3] [4
Non-PDF special ignored!
Non-PDF special ignored!] (./test.aux) )</usr/share/texmf-tetex/fonts/type1/blu
esky/cm/cmmi8.pfb></usr/share/texmf-tetex/fonts/type1/bluesky/cm/cmr8.pfb></usr
/share/texmf-tetex/fonts/type1/bluesky/cm/cmmi10.pfb></usr/share/texmf-tetex/fo
nts/type1/bluesky/cm/cmr9.pfb></usr/share/texmf-tetex/fonts/type1/bluesky/cm/cm
sy10.pfb></usr/share/texmf-tetex/fonts/type1/bluesky/cm/cmr10.pfb></usr/share/t
exmf-tetex/fonts/type1/bluesky/cm/cmbx10.pfb></usr/share/texmf-tetex/fonts/type
1/bluesky/cm/cmti10.pfb></usr/share/texmf-tetex/fonts/type1/bluesky/cm/cmsy8.pf
b></usr/share/texmf-tetex/fonts/type1/bluesky/cm/cmss12.pfb></usr/share/texmf-t
etex/fonts/type1/bluesky/cm/cmbx12.pfb>
Output written on test.pdf (4 pages, 72051 bytes).
Transcript written on test.log.

---

### Post by findik1 on 2006-12-28
Thanks also for the quick reply!
I am already using \usepackage{graphicx}. There is no problem with MikTeX. When I run winedt I was getting automatically a dvi file with aux file. From dvi I could see everything, I was later making dvipdf to see the text much clearer, actually yap-dvi viewer resoultion was alos great so I was mostly using dvi viewer for "quick checking" the mistakes.

Is this problem stg related to TeTeX?
thanks in advance

findik

---

### Post by NoNo_231 on 2006-12-28
As far as I know pdflatex and graphicx cannot handle eps files. The results above seem to be from the pdflatex command, not the latex command, else you should get test.dvi as a result. Thus they do not show what the problem could be with the latex procedure.

---

### Post by findik1 on 2006-12-28
To be clear, I typed on the termonal:
latex test.tex

I expected it would create test.dvi file. Am I wrong?

---

### Post by NoNo_231 on 2006-12-28
Also kile wil give the log and the error mesages at the log & messages window and the whole procedure at the output window.

---

### Post by findik1 on 2006-12-28
yes I also doubled check that. Similar results.
So this (e.g. dvi problem is nothing to do with Latex Version, or TeteX). Do I need extra packages? 

thank you

---

### Post by NoNo_231 on 2006-12-28
> **findik1 said:**
> 
Output written on test.pdf (4 pages, 72051 bytes).
Transcript written on test.log.

It says that it made the test.pdf file. I don't know why this is done. Maybe something in the document pushes to create pdf. I don't use the latex command too much and I don't use to create dvi documents for many reasons. One is the graphics and the different way of handling them and different formats needed. Also the pdflatex command produces better pdf duciments that dvips and dvipdf.

So I can not help you with this any more. I hope that someone else can. Maybe some googling will help. Maybe it could be a package that is to be used with pdflatex triggering the conversion, but really I don't know just assuming.

Hope I could help more.

---

### Post by findik1 on 2006-12-28
ok, thanks anyway.

Hi all,

does anybody know: 1. why there is no dvi created when you latex on terminal/kile?
2. pdf is created so that's also fine, I use pdf anyway. But why then eps figures is not shown, there are errors: "Non-PDF special ignored!" I cannot see eps figures for some reaons.
3. Should I get rid of tetex and install texlive? Does it make a difference?

thanks,
findik

---

### Post by NoNo_231 on 2006-12-28
I don't know if you need extra packages. Without any packages with the basic tetex installation the latex command should result to a .dvi file. Maybe you could download a file from the net, and try the latex command with this file to see if it file specific or there is a problem with tetex.
Or you could make a tex file with this
```

\documentclass[a4paper,10pt]{article}

\title{A small sample \dots}
\author{My, myself, and I}
\date{\today}

\begin{document}
\maketitle
\tableofcontents
...
\end{document}


```

save it and then run latex. It should create a dvi. If so, then there is something in the file making pdf. Else there is something tetex.

---

### Post by findik1 on 2006-12-28
that was a nice idea. I run your simple file and it created everything normally. So maybe problem is my conference journal style file: osajnl.sty

---

### Post by findik1 on 2006-12-28
I tested to take out osajnl.sty file then it works. THough I did not understand what is wrong with this style file with tetex. I have been using this journal style file about 3 years with MikTeX without any problem. 

Now another problem arised: I can see the eps figures from dvi and ps files but not from pdf.
Anybody knows the reason? Any suggestion about this and style file? 
appreciated
findik

---

### Post by findik1 on 2006-12-28
Hi all,
The issues related to dvi/pdf is resolved. Mainly style file.

However I still did not understand one main thing: while using Kile, when I use latex, then pdflatex (or quickbuild) eps figures are not seen in created pdf, but can be seen in created dvi or ps files. Is there a way to resolve this issue? Why Eps figures shows as blank in created pdf?

Thanks!

---

### Post by NoNo_231 on 2006-12-29
With kile you have to use the from tne build menu the forth menu, I have it in greek and can say for sure the english name, it could be conversion. There is Dvi2pdf (alt+9), dvi2ps (alt+4) and ps2pdf(alt+8 ). You can use these from the menu or with the key combinations.  The pdflatex file gives pdf from source not the dvi.

---

### Post by NoNo_231 on 2006-12-29
I checked it so it is in kile build>convert>--DVItoPDF
                                                          --DVItoPS
                                                          --PStoPDF

There is also button for all three of them, around the pdf button. The key combinations are also there to help you.

I think this is what you want :)

---

### Post by rasputin1575 on 2006-12-29
Sorry if someone has already told you how to repair it. i didnt go through all the replies.
but replying to your quote: 
[B]
"To be clear, I typed on the termonal:
latex test.tex

"I expected it would create test.dvi file. Am I wrong?"[/B]

no latex **doesnt** create dvi by default here (i mean through terminal)

ok first thing first,
if i were u, i would use kile/texmaker **only** to edit things, and **NOT** to run/complile etc.
thats because these editors have not been configured to understand the dvi/pdf..
of course u can configure them, but i suggest u browse through the net first and see hows its done.

what i ususally do (if am not using vi editor), i edit things in kile and then go back on terminal.
now what i noticed from ur previous post, caught my attention.
it seems that u type:
 latex test.tex

i would suggest u **dont **do that and type the following instead

**latex test**

then to see dvi, type

**xdvi test &**           (dont forget the & sign)

to convert to ps, type

**dvips test**

then to convert to pdf type,

**dvipdf test**


no need to tell u abt bbtex, am sure u know that u run bibtex test first THEN do 
latex test    (TWICE)

AND THE REST FOLLOWS..
Try these and lemme know what happens.

ash

---

### Post by joneberger on 2006-12-29
> **findik1 said:**
> Hi all,
The issues related to dvi/pdf is resolved. Mainly style file.

However I still did not understand one main thing: while using Kile, when I use latex, then pdflatex (or quickbuild) eps figures are not seen in created pdf, but can be seen in created dvi or ps files. Is there a way to resolve this issue? Why Eps figures shows as blank in created pdf?

Thanks!

Hey man.  I love LaTeX.  It's probably one of the more wonderful typesetting languages ever.

So if someone mentioned all of this, let me know.  So when I was looking through what you posted, I see this

> This is pdfeTeX, Version 3.141592-1.21a-2.2 (Web2C 7.5.4)
entering extended mode

This means that the editor was trying to compile to PdfLaTeX the file.  It would be the equivalent of you typing "pdflatex filename.tex" at the terminal.  The problem with this is if you use images in your .tex file, the pdflatex command looks for .pdf format images.  So if you're using encapsulated postscript files (.eps) you're in trouble.  (I see that someone has already recommended you use graphicx.  You definitely should to handle your images in documents.)  You can use epstopdf to convert your .eps images to .pdf format.  The command "latex filename.tex" should create a .dvi file, else you really have no output other than the .aux and a few other files bearing the same name as your file.  So if you want to view the .dvi (device independent, I believe) file, type "xdvi filename.dvi" as before mentioned.  I think that may have been a source of confusion from before that was already pointed out.

Good luck,

Jon

---

### Post by findik1 on 2006-12-29
Everything is very clear said, thank you very much for your help!
best
findik

---

### Post by QuITh on 2007-08-31
> **rasputin1575 said:**
> 
what i ususally do (if am not using vi editor), i edit things in kile and then go back on terminal.
now what i noticed from ur previous post, caught my attention.
it seems that u type:
 latex test.tex

i would suggest u **dont **do that and type the following instead

**latex test**

then to see dvi, type

**xdvi test &**           (dont forget the & sign)

to convert to ps, type

**dvips test**

then to convert to pdf type,

**dvipdf test**


no need to tell u abt bbtex, am sure u know that u run bibtex test first THEN do 
latex test    (TWICE)

AND THE REST FOLLOWS..
Try these and lemme know what happens.

ash

Why "latex test"?

---

### Post by lizz on 2008-06-04
I've just installed Kile (on Ubuntu) and for some reason it doesn't come with a couple of the packages I want (subfigure.sty and wrapfig.sty). I've created files in the usr/share/texmf-texlive/tex/latex and added in the subfigure (.sty and .cfg) and wrapfig.sty files into their respective folders but Kile still isn't picking up that they're there.

Can I either tell Kile where to look or install the packages another way? I've run through all the variations on sudo apt-get subfigure.sty etc that i can think of but given that I'm pretty new to this whole Linux thing I may well be missing something obvious...Unfortunately, the computer I was running Kile on before has Fedora rather than Ubuntu and so the set up is slightly different...

Cheers,
Liz

---

### Post by NoNo_231 on 2008-06-04
> **lizz said:**
> I've just installed Kile (on Ubuntu) and for some reason it doesn't come with a couple of the packages I want (subfigure.sty and wrapfig.sty). I've created files in the usr/share/texmf-texlive/tex/latex and added in the subfigure (.sty and .cfg) and wrapfig.sty files into their respective folders but Kile still isn't picking up that they're there.

Can I either tell Kile where to look or install the packages another way? I've run through all the variations on sudo apt-get subfigure.sty etc 

Hi Liz,

it seems that you need to install texlive-latex-extra from synaptic or through 
```
sudo apt-get install texlive-latex-extra
```
If you do a search in synaptic you will find them there under this package.

Regards,
Ilias

---


---
title: "Urgent! LaTeX/Kile install error"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by teHIngo on 2007-04-24
Hey guys!

First of all I want to thank everybody in advance. I've been using for about a week now, and I'm totally blown away!!

But now I've got a silly (yes, blame moe for that ;( ;)) problem:
I urgently need to get LaTeX running, because I need to hand out a Paper *the day after tomorrow*!!
That would be no problem so far, because if ubuntu wouldn't work I could just use Windows, eh? Yeah, could! But, you might already have guessed it, it crashed yesterday... Gone!

But to come to the problem...
I have followed the guide as described here: [http://ubuntuforums.org/showthread.php?t=141934](http://ubuntuforums.org/showthread.php?t=141934)
I am using the latest teXlive (2007) and the latest Kile under Ubuntu (Gnome).
However, after setting up everything as described in the Thread above, the compilation does not work. The errors follow:

> [LaTeX] yes.tex => yes.dvi (/usr/local/texlive/2007/bin/i386-linux/latex)
[LaTeX] finished with exit status 1
[LaTeX] 0 errors, 0 warnings, 0 badboxes

The output says:
> 
*****
*****     LaTeX output: 
*****     cd '/home/ingo'
*****     /usr/local/texlive/2007/bin/i386-linux/latex -src -interaction=nonstopmode 'yes.tex'
*****
This is pdfTeXk, Version 3.141592-1.40.3 (Web2C 7.5.6)
 Source specials enabled.
 %&-line parsing enabled.
kpathsea: Running mktexfmt latex.fmt
mktexfmt: running `pdfetex -ini   -jobname=latex -progname=latex -translate-file=cp227.tcx *latex.ini' ...
This is pdfeTeX, Version 3.141592-1.21a-2.2 (Web2C 7.5.4) (INITEX)
 (/usr/share/texmf-tetex/web2c/cp227.tcx)
entering extended mode
(/usr/share/texmf-tetex/tex/latex/config/latex.ini
(/usr/share/texmf-tetex/tex/generic/config/pdftexconfig.tex)
(/usr/share/texmf-tetex/tex/latex/base/latex.ltx
(/usr/share/texmf-tetex/tex/latex/base/texsys.cfg)
./texsys.aux found


\@currdir set to: ./.


Assuming \openin and \input 
have the same search path.


Defining UNIX/DOS style filename parser.

catcodes, registers, compatibility for TeX 2,  parameters,
LaTeX2e <2003/12/01>
hacks, control, par, spacing, files, font encodings, lengths,
====================================

Local config file fonttext.cfg used

====================================
(/usr/share/texmf-tetex/tex/generic/config/fonttext.cfg
(/usr/share/texmf-tetex/tex/latex/base/fonttext.ltx
=== Don't modify this file, use a .cfg file instead ===

(/usr/share/texmf-tetex/tex/latex/base/omlenc.def)
(/usr/share/texmf-tetex/tex/latex/base/t1enc.def)
(/usr/share/texmf-tetex/tex/latex/base/ot1enc.def)
(/usr/share/texmf-tetex/tex/latex/base/omsenc.def)
(/usr/share/texmf-tetex/tex/latex/base/t1cmr.fd)
(/usr/share/texmf-tetex/tex/latex/base/ot1cmr.fd)
(/usr/share/texmf-tetex/tex/latex/base/ot1cmss.fd)
(/usr/share/texmf-tetex/tex/latex/base/ot1cmtt.fd)))
====================================

Local config file fontmath.cfg used

====================================
(/usr/share/texmf-tetex/tex/generic/config/fontmath.cfg
(/usr/share/texmf-tetex/tex/latex/base/fontmath.ltx
=== Don't modify this file, use a .cfg file instead ===

(/usr/share/texmf-tetex/tex/latex/base/omlcmm.fd)
(/usr/share/texmf-tetex/tex/latex/base/omscmsy.fd)
(/usr/share/texmf-tetex/tex/latex/base/omxcmex.fd)
(/usr/share/texmf-tetex/tex/latex/base/ucmr.fd)))
====================================

Local config file preload.cfg used

=====================================
(/usr/share/texmf-tetex/tex/generic/config/preload.cfg
(/usr/share/texmf-tetex/tex/latex/base/preload.ltx)) page nos., x-ref,
environments, center, verbatim, math definitions, boxes, title, sectioning,
contents, floats, footnotes, index, bibliography, output,
===========================================
Local configuration file hyphen.cfg used
===========================================
(/usr/share/texmf-tetex/tex/generic/babel/hyphen.cfg
(/usr/share/texmf-tetex/tex/generic/hyphen/hyphen.tex)
(/usr/share/texmf-tetex/tex/generic/hyphen/frhyph.tex
frhyph.tex - French hyphenation patterns (V2.12) <2002/12/11>)
(/usr/share/texmf-tetex/tex/generic/hyphen/dehypht.tex
German Traditional Hyphenation Patterns `dehypht' Version 3.2a <1999/03/03>
(Formerly known under the name `ghyph31' and `ghyphen'.))
(/usr/share/texmf-tetex/tex/generic/hyphen/dehyphn.tex
New German Hyphenation Patterns `dehyphn' Rev.31 <2001-05-07> (WaS))
(/usr/share/texmf-tetex/tex/generic/hyphen/inhyph.tex)
(/usr/share/texmf-tetex/tex/generic/hyphen/bahyph.tex)
(/usr/share/texmf-tetex/tex/generic/bghyph/bghyphen.tex
Bulgarian hyphenation patterns
(/usr/share/texmf-tetex/tex/generic/bghyph/catmik.tex)
(/usr/share/texmf-tetex/tex/generic/bghyph/mik2t2.tex)
(/usr/share/texmf-tetex/tex/generic/bghyph/bghyphsi.tex))
(/usr/share/texmf-tetex/tex/generic/hyphen/cahyph.tex
Catalan Hyphenation Patterns `cahyphen' Version 1.11 <2003/07/15>)
(/usr/share/texmf-tetex/tex/generic/hyphen/hrhyph.tex)
(/usr/share/texmf-tetex/tex/generic/hyphen/czhyph.tex
(/usr/share/texmf-tetex/tex/csplain/t1code.tex Font encoding set to Cork.)
The \^, \`, \', \v, \" and \r expands to characters by Cork.
(/usr/share/texmf-tetex/tex/csplain/czhyphen.tex))
(/usr/share/texmf-tetex/tex/generic/hyphen/dkhyphen.tex
(/usr/share/texmf-tetex/tex/generic/hyphen/dkcommon.tex)
(/usr/share/texmf-tetex/tex/generic/hyphen/dkspecial.tex)
(/usr/share/texmf-tetex/tex/generic/hyphen/dkspecial.tex))
(/usr/share/texmf-tetex/tex/generic/hyphen/nehyph.tex)
(/usr/share/texmf-tetex/tex/generic/hyphen/eohyph.tex
Esperanto Hyphenation Patterns `eohyph', 1999-08-10)
(/usr/share/texmf-tetex/tex/generic/hyphen/eehyph.tex)
(/usr/share/texmf-tetex/tex/generic/hyphen/fi8hyph.tex)
(/usr/share/texmf-tetex/tex/generic/hyphen/grhyph.tex
Greek language hyphenation patterns)
(/usr/share/texmf-tetex/tex/generic/hyphen/icehyph.tex)
(/usr/share/texmf-tetex/tex/generic/hyphen/gahyph.tex
Hyphenation patterns `gahyph.tex' Version 1.0 <2004/01/22>)
(/usr/share/texmf-tetex/tex/generic/hyphen/ithyph.tex)
(/usr/share/texmf-tetex/tex/generic/hyphen/lahyph.tex
Latin Hyphenation Patterns `lahyph' Version 3.0b <2001/11/21>)
(/usr/share/texmf-tetex/tex/generic/hyphen/huhyphn.tex
Huhyphn - hungarian hyphenation patterns v20031107)
(/usr/share/texmf-tetex/tex/generic/hyphen/nohyphbx.tex
Hyphenation patterns for Norwegian)
(/usr/share/texmf-tetex/tex/generic/hyphen/plhyph.tex)
(/usr/share/texmf-tetex/tex/generic/hyphen/pt8hyph.tex
portuguese hiphenation 8 bits and -)
(/usr/share/texmf-tetex/tex/generic/hyphen/rohyphen.tex
Romanian Hyphenation Patterns: `rohyphen' 1.1 <29.10.1996>)
(/usr/share/texmf-tetex/tex/generic/ruhyphen/ruhyphen.tex
(/usr/share/texmf-tetex/tex/generic/ruhyphen/catkoi.tex)
(/usr/share/texmf-tetex/tex/generic/ruhyphen/koi2t2a.tex)
(/usr/share/texmf-tetex/tex/generic/ruhyphen/ruhyphal.tex)
(/usr/share/texmf-tetex/tex/generic/ruhyphen/cyryoal.tex)
(/usr/share/texmf-tetex/tex/generic/ruhyphen/hypht2.tex))
(/usr/share/texmf-tetex/tex/generic/hyphen/srhyphc.tex
Serbian Cyrillic Hyphenation Patterns `srhyphc.tex' v1.0a <2003-06-09>)
(/usr/share/texmf-tetex/tex/generic/hyphen/skhyph.tex
(/usr/share/texmf-tetex/tex/csplain/t1code.tex Font encoding set to Cork.)
The \^, \`, \', \v, \" and \r expands to characters by Cork.
(/usr/share/texmf-tetex/tex/csplain/skhyphen.tex))
(/usr/share/texmf-tetex/tex/generic/hyphen/sihyph23.tex
Slovene Hyphenation Patterns `sihyph23' Version 2.3 <97/15/04>)
(/usr/share/texmf-tetex/tex/generic/hyphen/eshyph.tex)
(/usr/share/texmf-tetex/tex/generic/hyphen/sehyph.tex
Swedish hyphenation patterns, Jan Michael Rynning, 1994-03-03.)
(/usr/share/texmf-tetex/tex/generic/hyphen/trhyph.tex
Turkish Hyphenation Patterns `trhyph' Version 1.0a <97/05/04>)
(/usr/share/texmf-tetex/tex/generic/ukrhyph/ukrhyph.tex
Ukrainian hyphenation patterns in t2a encoding
(/usr/share/texmf-tetex/tex/generic/ukrhyph/catlcy.tex)
(/usr/share/texmf-tetex/tex/generic/ukrhyph/lcy2t2a.tex)
(/usr/share/texmf-tetex/tex/generic/ukrhyph/ukrhypmp.tex)
(/usr/share/texmf-tetex/tex/generic/ruhyphen/hypht2.tex))
(/usr/share/texmf-tetex/tex/generic/hyphen/zerohyph.tex))
=================================
Applying patch file ltpatch.ltx
=================================
(/usr/share/texmf-tetex/tex/latex/base/ltpatch.ltx)
 ) )
Beginning to dump on file latex.fmt
 (format=latex 2007.4.24)
5499 strings of total length 74189
47474 memory locations dumped; current usage is 144&43215
3273 multiletter control sequences
\font\nullfont=nullfont
\font\OMX/cmex/m/n/10=cmex10
\font\tenln=line10
\font\tenlnw=linew10
\font\tencirc=lcircle10
\font\tencircw=lcirclew10
\font\OT1/cmr/m/n/5=cmr5
\font\OT1/cmr/m/n/7=cmr7
\font\OT1/cmr/m/n/10=cmr10
\font\OML/cmm/m/it/5=cmmi5
\font\OML/cmm/m/it/7=cmmi7
\font\OML/cmm/m/it/10=cmmi10
\font\OMS/cmsy/m/n/5=cmsy5
\font\OMS/cmsy/m/n/7=cmsy7
\font\OMS/cmsy/m/n/10=cmsy10
3633 words of font info for 14 preloaded fonts
580 hyphenation exceptions
Hyphenation trie of length 150552 has 3904 ops out of 35111
  138 for language 32
  12 for language 31
  127 for language 30
  76 for language 29
  71 for language 28
  248 for language 27
  62 for language 26
  119 for language 25
  68 for language 24
  7 for language 23
  194 for language 22
  756 for language 21
  117 for language 20
  26 for language 19
  35 for language 18
  229 for language 17
  147 for language 16
  6 for language 15
  31 for language 14
  113 for language 13
  145 for language 12
  265 for language 11
  60 for language 10
  63 for language 9
  19 for language 8
  21 for language 7
  12 for language 6
  5 for language 5
  21 for language 4
  235 for language 3
  207 for language 2
  88 for language 1
  181 for language 0
No pages of output.
Transcript written on latex.log.
mktexfmt: /home/ingo/.texmf-var/web2c/latex.fmt installed.
---! /home/ingo/.texmf-var/web2c/latex.fmt was written by pdfetex
(Fatal format file error; I'm stymied)


Please help me and make me a happy Ubuntu user!! :(

---

### Post by tkjacobsen on 2007-04-24
Do you use feisty?

Then maybe you should try the texlive install from the repositories, the howto you have followed is probably for dapper.  It is working great for me..

You should install texlive before kile, since kile will try to install tetex if no latex distribution is installed. (That's why you had to do all the tricks in dapper.)


Hope this helps you

---

### Post by metra on 2007-04-24
I'm sorry I can't help you with your actually problem, but I think you might get some attention from people who do know if you have a more specific subject. Such Urgent! LaTeX/Kile install error.

I checked out your post out of curiosity but you probably need to get the attention of someone who uses those apps.

---

### Post by teHIngo on 2007-04-25
> **metra said:**
> I'm sorry I can't help you with your actually problem, but I think you might get some attention from people who do know if you have a more specific subject. Such Urgent! LaTeX/Kile install error.

I checked out your post out of curiosity but you probably need to get the attention of someone who uses those apps.

Okay, thanks for that, I'll keep that in mind the next time! :)

//Edit:

Oh, and just checked it out: IT'S WORKING!! THANK YOU VERY MUCH! :)

---

### Post by frisket on 2007-04-27
> **teHIngo said:**
> 
I am using the latest teXlive (2007) and the latest Kile under Ubuntu (Gnome).
However, after setting up everything as described in the Thread above, the compilation does not work. The errors follow:
(

Looks like you didn't complete the TeXLive installation by running texconfig, so there was no format (.fmt) file, so it tried to make one. I don't know why it didn't run texconfig when it installed (mine did), but if you run it now, set up your printer, defaults paper size, margins, offsets, etc, it should end up by creating the right .fmt files in the right places (do it as root).

Or indeed install from Ubuntu packages, although that doesn't give you all the works, and it puts stuff in weird places. But it should work out of the box.

---

### Post by venik212 on 2007-05-12
"But it should work out of the box."
I could not agree with you more, but it does not.  I installed TexLive from the Kubuntu packages, then ran Texconfig, then intalled Kile, but  it works only for small projects when all the relevant files are in the working directory.  If the Latex file needs a package from another directory, Kile is clueless.  
It did work, in the pastm using tetex, but it seems oblivious to TexLive;-(

---


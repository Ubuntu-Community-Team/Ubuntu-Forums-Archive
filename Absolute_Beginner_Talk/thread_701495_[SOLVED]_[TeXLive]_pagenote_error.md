---
title: "[SOLVED] [TeXLive] pagenote error"
date: 2008-02-19
forum: Absolute Beginner Talk
---

### Post by Jodi on 2008-02-19
I am trying to get texlive to work on my Gutsy installation... I want to work on my thesis at home; at my work (CentOS linux) it compiles perfectly. Now when I compile my tex files, latex starts barfing. I have never seen an error like this:
```
This is pdfTeXk, Version 3.141592-1.40.3 (Web2C 7.5.6)
 %&-line parsing enabled.
entering extended mode
(./thesis.tex
LaTeX2e <2005/12/01>
Babel <v3.8h> and hyphenation patterns for english, usenglishmax, dumylang, noh
yphenation, croatian, bulgarian, russian, ukrainian, czech, slovak, danish, dut
ch, finnish, finnish, french, basque, french, german, ngerman, german, ngerman,
 greek, monogreek, ancientgreek, ibycus, hungarian, hungarian, italian, italian
, latin, latin, mongolian, mongolian, norsk, norsk, coptic, esperanto, estonian
, icelandic, indonesian, interlingua, romanian, serbian, slovenian, turkish, up
persorbian, welsh, polish, polish, portuguese, portuguese, spanish, catalan, ga
lician, spanish, catalan, galician, swedish, swedish, loaded.
(./memoir.cls
Document Class: memoir 2004/01/31 v1.6 configurable document class
(/usr/share/texmf-texlive/tex/latex/memoir/mem11.clo)
(/usr/share/texmf-texlive/tex/latex/memoir/mempatch.sty
! Undefined control sequence.
l.1195 \EmulatedPackage
                       {pagenote}
?
```
When I check /usr/share/texmf-texlive/tex/latex for a pagenote directory, it is actually there:
```
drwxr-xr-x 2 root root  4096 2008-02-19 17:26 pagenote
```
It even contains a pagenote.sty file :|

According to [this page]("http://packages.ubuntu.com/hardy/tex/texlive-latex-extra"), texlive-latex-extra holds the pagenote package. This has been installed as requirement for one of the latex packages. Reinstalling texlive-latex-extra doesn't help.

The texconfig conf command does not show any errors, rehashing doesn't help, Google holds no answers, apparently nobody EVER lost his pagenote package. I have no clue where to start solving this problem. I have installed texlive with Aptitude, no luck. Removed it, installed with apt-get, no luck. Removed it, installed with aptitude, no luck. Removed it, installed with synaptic, no luck.

My installed TeX packages:
```

dpkg -l | grep texlive
ii  texlive                                    2007-10                                   TeX Live: A decent selection of the TeX Live
ii  texlive-base                               2007-10                                   TeX Live: Essential programs and files
ii  texlive-base-bin                           2007-12ubuntu3.1                          TeX Live: Essential binaries
ii  texlive-bibtex-extra                       2007-3                                    TeX Live: Extra BibTeX styles
ii  texlive-common                             2007-10                                   TeX Live: Base component
ii  texlive-doc-base                           2007-3                                    TeX Live: Base documentation
rc  texlive-doc-nl                             2007-3                                    TeX Live: Dutch documentation
rc  texlive-extra-utils                        2007-12ubuntu3.1                          TeX Live: TeX auxiliary programs
ii  texlive-font-utils                         2007-12ubuntu3.1                          TeX Live: TeX font-related programs
ii  texlive-fonts-extra                        2007-3                                    TeX Live: Extra fonts
ii  texlive-fonts-recommended                  2007-10                                   TeX Live: Recommended fonts
rc  texlive-formats-extra                      2007-3                                    TeX Live: Extra formats
ii  texlive-generic-extra                      2007-3                                    TeX Live: Miscellaneous extra generic macros
ii  texlive-generic-recommended                2007-10                                   TeX Live: Miscellaneous generic macros
rc  texlive-humanities                         2007-3                                    TeX Live: LaTeX support for the humanities
ii  texlive-lang-croatian                      2007.dfsg.1-3                             TeX Live: Croatian
ii  texlive-lang-cyrillic                      2007.dfsg.1-3                             TeX Live: Cyrillic
ii  texlive-lang-czechslovak                   2007.dfsg.1-3                             TeX Live: Czech/Slovak
ii  texlive-lang-danish                        2007.dfsg.1-3                             TeX Live: Danish
ii  texlive-lang-dutch                         2007.dfsg.1-3                             TeX Live: Dutch
ii  texlive-lang-finnish                       2007.dfsg.1-3                             TeX Live: Finnish
ii  texlive-lang-french                        2007.dfsg.1-3                             TeX Live: French
ii  texlive-lang-german                        2007.dfsg.1-3                             TeX Live: German
ii  texlive-lang-greek                         2007.dfsg.1-3                             TeX Live: Greek typesetting
ii  texlive-lang-hungarian                     2007.dfsg.1-3                             TeX Live: Hungarian
ii  texlive-lang-italian                       2007.dfsg.1-3                             TeX Live: Italian
ii  texlive-lang-latin                         2007.dfsg.1-3                             TeX Live: Latin
ii  texlive-lang-mongolian                     2007.dfsg.1-3                             TeX Live: Mongolian
ii  texlive-lang-norwegian                     2007.dfsg.1-3                             TeX Live: Norwegian
ii  texlive-lang-other                         2007.dfsg.1-3                             TeX Live: Other hyphenation files
ii  texlive-lang-polish                        2007.dfsg.1-3                             TeX Live: Polish
ii  texlive-lang-portuguese                    2007.dfsg.1-3                             TeX Live: Portuguese
ii  texlive-lang-spanish                       2007.dfsg.1-3                             TeX Live: Spanish
ii  texlive-lang-swedish                       2007.dfsg.1-3                             TeX Live: Swedish
ii  texlive-lang-vietnamese                    2007.dfsg.1-3                             TeX Live: Vietnamese
ii  texlive-latex-base                         2007-10                                   TeX Live: Basic LaTeX packages
ii  texlive-latex-extra                        2007-3                                    TeX Live: LaTeX supplementary packages
ii  texlive-latex-recommended                  2007-10                                   TeX Live: LaTeX recommended packages
ii  texlive-math-extra                         2007-3                                    TeX Live: Advanced math typesetting
rc  texlive-omega                              2007-12ubuntu3.1                          TeX Live: Omega
ii  texlive-pictures                           2007-10                                   TeX Live: Packages for drawings graphics
rc  texlive-plain-extra                        2007-3                                    TeX Live: Plain TeX supplementary packages
ii  texlive-pstricks                           2007-3                                    TeX Live: PSTricks packages
ii  texlive-publishers                         2007-3                                    TeX Live: Support for publishers
rc  texlive-science                            2007-3                                    TeX Live: Typesetting for natural and comput
rc  texlive-xetex                              2007-12ubuntu3.1                          TeX Live: XeTeX macros

```
Does anyone have a clue? I'm going insane here, any help is appreciated!

---

### Post by Jodi on 2008-02-21
Little bump... Nobody?

Still looking for a solution, still found nothing... And I *really* would like to work on my Master's thesis at home :)

Maybe I posted this in the wrong subforum; if so, mods, please feel free to move this thread. Sorry if I maybe misplaced this thread!

---

### Post by Jodi on 2008-02-22
Ah, success... Sort of.

The LaTeX template used by my research group apparantly is based on teTeX, and included some form of memoir class. TeXLive has its own memoir class, and these two were in each other's way: the teTeX memoir class wanted some function, which is not provided by TeXLive. Using TeXLive's own memoir class solved the problem.... Only to leave me with another "feature" of TeXLive: I need both the memoir and fancyhdr (former fancyheaders) packages, and these two are conflicting. Both define a function with the same name. Another problem :)

Anyway, initial problem solved. If you get a standard set of template files, make sure they are TeXLive-compatible...

---

### Post by vahidg on 2008-04-01
In fancyhdr.sty find the command which is causing the problem and change 'newcommand' to 'renewcommand'.

---


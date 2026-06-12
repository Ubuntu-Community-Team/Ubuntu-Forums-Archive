---
title: "'MnSymbol.sty' not found"
date: 2008-03-12
forum: Absolute Beginner Talk
---

### Post by alexandra_k on 2008-03-12
I'm trying to install Minion Pro fonts on LaTex.

I apologize if this is the wrong forum to post this on...

I've got a test to see whether it is installed correctly:

\documentclass{article}
\usepackage{MnSymbol}
\usepackage{MinionPro}
\usepackage[mathlf,textlf,minionint]{MinionPro}
\usepackage[T1]{fontenc}
\usepackage{textcomp}
\begin{document}
The quick brown fox jumps over the lazy dog.
\end{document}

I'm getting an error message when I typeset:

! LaTex Error:  File `MnSymbol.sty' not found.

My problem is that I don't have a MnSymbol.sty file. 
The .sty files that I have are:

fontaxes
MinionPro
otfontdef

And that is all.  Am I missing something???

What does MnSymbol.sty do??  Can I do without it?

Another issue...  Do I really really really need to rename the files so they are in the Berry system?  I haven't done this...  Is it about aesthetics or about the program running?  (There are many many files and I'm dreading the thought of having to find out what name to replace them with and then doing that manually.  Talking about thousands of files here...)

---

### Post by glennric on 2008-03-12
You can download the file Mnsymbol.zip from [ftp://cam.ctan.org/tex-archive/fonts/Mnsymbol.zip]("ftp://cam.ctan.org/tex-archive/fonts/Mnsymbol.zip")
Then unzip the file and follow the directions in the README.  You can use the directory ~/texmf to install the files to, creating the appropriate directory structure according to the README inside that.  If you need help I am going to try to do it too, and will help you.  I have done this before so it shouldn't be a problem for me.

---

### Post by glennric on 2008-03-12
Ok, so I got MnSymbol.sty setup, but then you will have to install MinionPro.sty as well.  If you have done that then you are good to go.

---

### Post by alexandra_k on 2008-03-13
Thanks so much for your response!  I have downloaded from the link you provided and I'm about to try following the (surprisingly comprehensible sounding) instructions now.

Probably take me about a day (have some other stuff I need to do).

But I'll get back to you with respect to my success or failure.

Thanks so much.

---

### Post by glennric on 2008-03-13
I have created scripts to install and uninstall both MnSymbol and MinionPro.  They are attached below.  Put them in the same directory as the zip files mnsymbol.zip and minionpro.zip.  For minionpro you will also have to obtain the otf files.  You can get them from the acroread installation.  They are in the directory /usr/lib/Adobe/Reader8/Resource/Font.  Put them in a directory AdobeOTF, which should be in the same directory as the zip files.  Then run
```
./install-mnsymbol
./install-minionpro
```
To uninstall use
```
./uninstall-minionpro
./uninstall-mnsymbol
```
If you have any problems let me know.

Edit:  Added the attachments.  You should put the tar file in the zip directory and run
```
tar xzvf minionpro-scripts.tar.gz
```

---

### Post by alexandra_k on 2008-03-13
Wow.

So I just found your latest post now.  Where I'm at...  I think I installed things okay (from the CTAN link), but now I'm getting an error message:

!LaTex Error:  Command `h\bar' already defined.

Would there be a simple solution for that?
If not...

Then I could have a go at following the instructions in your last post.

Trouble is that I really am very computer illiterate...  I'm concerned about some of the things I've done...  For example...  It said to put the MinionPro fonts into the local directory (to save them being overwritten).  It didn't say to put the MinionPro Symbol fonts into the local directory...  But I put them there anyway...

Any thoughts on the error command?

(I'm getting that from running the test that I posted in my first post).  A couple of other things like:

LaTeX Font Warning:  Encoding `OT1' has changed to `T1' for symbol font
(Font)  `operators' in the math version `bold' on input line 111.

But not sure those matter...

It is producing a PDF when I typeset - but I can't see any of the sample text (or anything else) on the PDF...

---

### Post by alexandra_k on 2008-03-13
I should perhaps say that I acquired the MinionPro fonts that I'm installing off a friend.  He had them on a CD where they were already converted into the right kind of file.  All I needed to do was to create a directory tree in the local tex tree... And copy paste the files in there.  My friend had a map file already so I went with that (which might be a problem).

Then someone else used terminal to update the map and something like...  Getting tex to check the new directory / map...  

Was worried about using his map...  But I wasn't sure on the instructions for downloading the program...  And generating my own one.  My friend installed on PC (MikiTex) whereas I have the texlive package for Mac.

Seems to be ok though apart from not having Symbol fonts.
But now those seem to be okay apart from the hbar thing....

Trouble is...

I didn't install the files in the zipped version (I created the directories manually and copy pasted the files into them) since I don't really know how to use terminal.

And...  I'm not quite sure what I'm supposed to do with (where I'm supposed to put) the zipped files...)

People tried telling me that I probably couldn't do this...
Oopsie...

Pretty font though :-)

---

### Post by glennric on 2008-03-17
So you are using texlive on a mac, and not on Ubuntu?  Things should be similar there, but there may be subtle differences that can cause a problem.  I actually made debian packages to install these fonts in Ubuntu, but those won't work on a mac.  The scripts I posted should work, but I think there might have been an error in those.  I will have to check.  The font warning you are getting is not a problem.  I get that too, but the fonts still work.  I also got the blank pdf documents for a while.  It turned out it was a conflict between the user font map and the system wide font map.  Try running both "updmap" and "sys updmap-sys".  That should fix the blank pdf thing.  I don't know about your h\bar error.

---

### Post by glennric on 2008-03-17
Here are updated scripts that should install everything correctly.

---

### Post by alexandra_k on 2008-03-21
Thank you so much for your time, I really appreciate it.  Part of the problem I'm having is that I'm not sure where to install things.  The instructions say to install things to:

.../texmf/fonts/source/public/MnSymbol/

I'm not sure exactly where on the tree texmf belongs, however.  I've tried installing them (one at a time) to the following three places and even after running mktexlsr and updmap-sys --enable MixedMap.MnSymbol.map the font doesn't seem to have installed correctly (errors on the MnSymbol test program).

I tried to put them here:

usr/local/texlive/texmf-local/

then I deleted them from there and tried to put them here (following instructions I found someplace).

usr/local/share/texmf/  (where I had to make the texmf folder myself)

then I deleted them from there and tried to put them here (because updmap etc seem to be looking through the 2007 files and folders only)

usr/local/texlive/2007/texmf

I even tried to put them here:

usr/local/texlive/2007/texmf-local (where I made the texmf-local folder myself).

And none of those locations seemed to work...

Where is the dvips, fonts, tex etc folders supposed to go?  Which folder and where?  Sorry I'm so dense about this :-(

---

### Post by alexandra_k on 2008-03-25
I think this might be approximating a minimal example of the problem (sorry it took me so long to get to this).

If I try and compile this simple template:

\documentclass{article}
\usepackage{MnSymbol}
\begin{document}
$x+1$
\end{document}

I get a PDF generated with this error log:

This is pdfTeXk, Version 3.141592-1.40.3 (Web2C 7.5.6)
 \write18 enabled.
 %&-line parsing enabled.
entering extended mode
(./mnsymbol-test.tex
LaTeX2e <2005/12/01>
Babel <v3.8h> and hyphenation patterns for english, usenglishmax, dumylang, noh
yphenation, arabic, basque, bulgarian, coptic, welsh, czech, slovak, german, ng
erman, danish, esperanto, spanish, catalan, galician, estonian, farsi, finnish,
 french, greek, monogreek, ancientgreek, croatian, hungarian, interlingua, ibyc
us, indonesian, icelandic, italian, latin, mongolian, dutch, norsk, polish, por
tuguese, pinyin, romanian, russian, slovenian, uppersorbian, serbian, swedish, 
turkish, ukenglish, ukrainian, loaded.
(/usr/local/texlive/2007/texmf-dist/tex/latex/base/article.cls
Document Class: article 2005/09/16 v1.4f Standard LaTeX document class
(/usr/local/texlive/2007/texmf-dist/tex/latex/base/size10.clo))
(/usr/local/texlive/2007/../texmf-local/tex/latex/MnSymbol/MnSymbol.sty
(/usr/local/texlive/2007/texmf-dist/tex/latex/amsmath/amsmath.sty
For additional information on amsmath, use the `?' option.
(/usr/local/texlive/2007/texmf-dist/tex/latex/amsmath/amstext.sty
(/usr/local/texlive/2007/texmf-dist/tex/latex/amsmath/amsgen.sty))
(/usr/local/texlive/2007/texmf-dist/tex/latex/amsmath/amsbsy.sty)
(/usr/local/texlive/2007/texmf-dist/tex/latex/amsmath/amsopn.sty))
(/usr/local/texlive/2007/texmf-dist/tex/latex/base/textcomp.sty
(/usr/local/texlive/2007/texmf-dist/tex/latex/base/ts1enc.def))
(/usr/local/texlive/2007/texmf-dist/tex/latex/amsfonts/eufrak.sty)

LaTeX Font Warning: Encoding `OMS' has changed to `U' for symbol font
(Font)              `symbols' in the math version `normal' on input line 120.


LaTeX Font Warning: Encoding `OMS' has changed to `U' for symbol font
(Font)              `symbols' in the math version `bold' on input line 120.

) (./mnsymbol-test.aux)
(/usr/local/texlive/2007/texmf-dist/tex/latex/base/ts1cmr.fd) [1{/Users/alexandra/.
texlive2007/texmf-var/fonts/map/pdftex/updmap/pdftex.map}] (./mnsymbol-test.aux
)kpathsea: Running mktexpk --mfmode / --bdpi 600 --mag 1+0/600 --dpi 600 MnSymbolC10
mkdir: ././Users/alexandra/.texlive2007/texmf-var/fonts/pk: Permission denied
mktexpk: mktexdir /Users/alexandra/.texlive2007/texmf-var/fonts/pk/ljfour/public/MnSymbol failed.
kpathsea: Appending font creation commands to missfont.log.
 )

pdfTeX warning: /usr/texbin/pdflatex (file MnSymbolC10): Font MnSymbolC10 at 60
0 not found
</usr/local/texlive/2007/texmf-dist/fonts/type1/bluesky/cm/cmmi10.pfb></usr/loc
al/texlive/2007/texmf-dist/fonts/type1/bluesky/cm/cmr10.pfb>
Output written on mnsymbol-test.pdf (1 page, 5464 bytes).
Transcript written on mnsymbol-test.log.

I'm getting jolly temped to trash the whole TexLive installation and try downloading it again...  But it is a very big (and complicated) installation...

---


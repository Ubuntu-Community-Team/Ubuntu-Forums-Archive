---
title: "latex, setspace, doublespacing"
date: 2007-12-02
forum: Absolute Beginner Talk
---

### Post by goodmanbrown on 2007-12-02
I re-installed Gutsy last week, and now I'm having a strange problem with LaTeX.  I've never learned anything about how to set up LaTeX (it's always just worked) so I'm at a loss to troubleshoot.  I'm hoping someone has seen this behavior before and can point me in the right direction.

I'm trying to get double-spacing working.  I've installed texlive-latex-recommended, which includes the setspace package.  My preamble goes:

```
\documentclass[letterpaper,12pt,oneside]{memoir}
\usepackage[headings]{fullpage}
\usepackage{setspace}

\doublespacing

\title{}
\author{}
\date{}

\begin{document}
```

When I try to compile this, LaTeX fails and I get the error message:

```
ERROR: Undefined control sequence.

--- TeX said ---
l.6 \doublespacing
                  
--- HELP ---
TeX encountered an unknown command name. You probably misspelled the
name. If this message occurs when a LaTeX command is being processed,
the command is probably in the wrong place---for example, the error
can be produced by an \item command that's not inside a list-making
environment. The error can also be caused by a missing \documentclass
command.
```

So it can find the setspace package, but not the \doublespacing command it provides.  If I remove the \doublespacing line from the preamble, the document compiles just fine.  If, instead of using \doublespacing in the preamble, I use \begin{doublespace} ... \end{doublespace} in the body of the document, I get the same sort of error:

```
ERROR: LaTeX Error: Environment doublespace undefined.

--- TeX said ---

See the LaTeX manual or LaTeX Companion for explanation.
Type  H <return>  for immediate help.
 ...                                              
                                                  
l.20 \begin{doublespace}
                        
--- HELP ---
LaTeX has encountered a \begin command for a nonexistent environment.
You probably misspelled the environment name. 
```

Does anyone know where the problem has crept in, and how I might fix it?  Thanks in advance for any help.

---

### Post by goodmanbrown on 2007-12-03
One additional bit of information:

If I copy setspace.sty from its home in /usr/share/texmf-texlive/tex/latex/setspace/ to my working directory, and then tell my tex file to look for it in my working directory, everything compiles just fine.  So it seems that LaTeX can find the memoir class in
```
/usr/share/texmf-texlive/tex/latex/memoir/
```

but can't find the setspace package in 
```
/usr/share/texmf-texlive/tex/latex/setspace/
```

Any idea why that could be?

---

### Post by elyob on 2008-05-24
Use the command "\DoubleSpacing".  Memoir actually ignores any \usepackage or \RequirePackage related to setspace.  (See TUGBoat, Volume 28, No. 2, p. 245.)

It also does this with
abstract, appendix, array, booktabs, ccaption, 
chngcntr, chngpage, dcolumn, delarray, enumerate, 
epigraph, framed, ifmtarg, ifpdf , index, makeidx, 
moreverb, needspace, new&#64257;le, nextpage, parskip, 
patchcmd, shortvrb, showidx, tabularx, 
titleref , titling, tocbibind, tocloft, verbatim, verse

---


---
title: "latex and Texmaker cls not found"
date: 2008-04-03
forum: Absolute Beginner Talk
---

### Post by myotis on 2008-04-03
With 7.1 I follwoed instructions elswhere to install Latex and TexMaker

sudo apt-get install texlive texmaker

When I try to quickcompile a simple doc in Texmaker

\documentclass(article)
\begin(document)
this is some sample text
\end(document)

I get an error:

%&-line parsing enabled.
**newtest.tex
(./newtest.tex
LaTeX2e <2005/12/01>
Babel <v3.8h> and hyphenation patterns for english, usenglishmax, dumylang, noh
yphenation, loaded.
! LaTeX Error: File `(.cls' not found.
Type X to quit or <RETURN> to proceed,
or enter new name. (Default extension: cls)
Enter file name:
! Emergency stop.
<read *>
l.1 \documentclass(a
rticle)^^M
*** (cannot \read from terminal in nonstop modes)
Here is how much of TeX's memory you used:

Suggesting it cannot find the class file or indeed mybe not finding Latex. Are there other aspects of configuration I should be following.

Many thanks,

Graham

---

### Post by myotis on 2008-04-03
To reply to myself, I have now installed the meta package through synaptic and this is now working. Not perfectly, but I can tweak away at the other issues, now that I have the basics working.

However, I suspect it has a lot more to do with me using the correct type of brackets the second time around. How stupid am I !!!!

Graham

---


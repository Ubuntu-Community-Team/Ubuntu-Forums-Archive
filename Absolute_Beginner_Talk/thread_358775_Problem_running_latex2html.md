---
title: "Problem running latex2html"
date: 2007-02-11
forum: Absolute Beginner Talk
---

### Post by Aktrop on 2007-02-11
Hi,

I'm trying to run latex2html in Kile on a .tex file, but the output says:

*****
*****     LaTeXtoHTML output: 
*****     cd '/home/Aktrop/My Documents/My eBooks/even newer webpages'
*****     latex2html 'Latex2HtmlCV.tex'
*****
This is LaTeX2HTML Version 2002-2-1 (1.71)
by Nikos Drakos, Computer Based Learning Unit, University of Leeds.

Revised and extended by:
 Marcus Hennecke, Ross Moore, Herb Swan and others
...producing markup for HTML version 4.0  


Extension: loading /usr/share/latex2html/versions/latin1.pl
HTML version: loading /usr/share/latex2html/versions/html4_0.pl

 *** processing declarations ***

OPENING /home/Aktrop/My Documents/My eBooks/even newer webpages/Latex2HtmlCV.tex 
Cannot create directory Latex2HtmlCV/: File exists, reusing it.

Note: Working directory is /home/Aktrop/My Documents/My eBooks/even newer webpages/Latex2HtmlCV
Note: Images will be generated in /tmp/l2h9312

texexpand V2002-2-1 (Revision 1.12)

texexpand: Error: More than one input file specified.
 texexpand  failed: No such file or directory

Any thoughts on how to fix this would be much appreciated!

-Aktrop

---

### Post by aprotim on 2007-03-01
There's a bug that causes problems when running latex2html on files which have spaces in the path.  The workaround is to either move things to folders with no spaces, or add appropriate symbolic links.

---


---
title: "TexMaker does not display the full log file"
date: 2007-09-05
forum: Absolute Beginner Talk
---

### Post by stefangachter on 2007-09-05
I am new to TexMaker, TexLive 2007 and Ubuntu 7.04 and I am wondering, if this is the correct behavior or not:

When I compile a document in TexMaker (latex or pdflatex), and if there is an error in the document, TexMaker does not display the log file, but only the start and end message:

Process started

Process exited with error(s)

The same non-informative behavior is the case, even then the document has no error:

Process started

Process exited normally

The log file is only displayed when I execute the Quick Build command, but only after I close the viewer. Actually, TexMaker waits until the viewer is close otherwise it's not possible to continue to edit the text.

Here are the command entires:

latex -interaction=nonstopmode %.tex
pdflatex -interaction=nonstopmode %.tex
pdflatex -interaction=nonstopmode %.tex|bibtex %.aux|pdflatex -interaction=nonstopmode %.tex|pdflatex -interaction=nonstopmode %.tex|evince %.pdf

Has anybody made similar experiencies? Anybody a hint how to fix this?

Thanks, Stefan

---

### Post by vrangforestillinger on 2008-04-06
*bump*

I have the same problem.

---

### Post by barnex on 2008-06-04
Same here, trying to solve it.

---

### Post by barnex on 2008-06-04
**Solution: ** If you use the 'Quick Build' command (which you can configure to execute a sequence of commands such as: compile + view), then the full output is automatically shown.
Cheers.

---


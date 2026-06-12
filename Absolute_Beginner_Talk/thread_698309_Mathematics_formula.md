---
title: "Mathematics formula"
date: 2008-02-16
forum: Absolute Beginner Talk
---

### Post by reesy on 2008-02-16
I was wondering if any one could suggest any software for writing maths formulas . I have been using open office to do my maths course work but can not find all of the special characters I need to write my formulas. 
Here is and example of the sort of formulas I will need to be able to write.
[[img]http://img2.freeimagehosting.net/uploads/3b791d3d53.gif[/img]](http://www.freeimagehosting.net/)
Thanks.

---

### Post by klytu on 2008-02-16
> **reesy said:**
> I was wondering if any one could suggest any software for writing maths formulas . I have been using open office to do my maths course work but can not find all of the special characters I need to write my formulas. 
Here is and example of the sort of formulas I will need to be able to write.
[[img]http://img2.freeimagehosting.net/uploads/3b791d3d53.gif[/img]](http://www.freeimagehosting.net/)
Thanks.

Check out the OpenOffice.org Math help section. You may find what you need there. An example of how to get there - open up, say, OpenOffice writer. Hit F1, then select OpenOffice.org Math in the dropdown menu at the upper left. Then click the link for formula reference table on the right. 

Hope this helps.

EDIT: Here's how to write the exact formula in your post using OpenOffice.org writer. Cut and paste this into a blank OpenOffice writer document:

```
%sigma = SQRT {{{%SIGMA {({ x &#8211; overline x }) sup 2}} over n}}
```

Then highlight the whole thing. Now go to the toolbar and choose Insert>Object>formula.

---

### Post by bwiklak on 2008-02-16
Hej, I'm writing my masters thesis in Tex (LaTex), but it is little complicated. If you like coding and you are not afraid of not wysywyg editors you should try, if not OpenOffice is the best.

---

### Post by dvase on 2008-02-17
> **bwiklak said:**
> Hej, I'm writing my masters thesis in Tex (LaTex), but it is little complicated. If you like coding and you are not afraid of not wysywyg editors you should try, if not OpenOffice is the best.

I'll second the LaTeX recommendation. It's not for everyone, but the results, especially the math equations are quite beautiful.

---

### Post by Whiffle on 2008-02-17
As far as I'm concerned, if you're serious about writing math formulas, LaTeX is the only way to go.  Once you get comfortable with it, its much more powerful than any WYSIWYG word processor can dream of.   It looks nicer too.

---

### Post by hardyn on 2008-02-17
But if you not really serious... open office is REALLY good... i used it thougout my uni career.  It is one feature that kicks the SH! out of ms-office.

---

### Post by spacefreak86 on 2008-02-17
Definitely go for LaTeX. There is a learning curve on it, but there are many templates on the web to search for that will help you out with it. I'm using lab reports to teach myself LaTeX as I go along, and so far its not too bad.

---

### Post by sofos on 2008-02-20
Hello,
 I have just started using Ubuntu and I really have minimum knowledge about Latex.
A friend installed it to my laptop but I don't really know how can I even start.
What should I do to write a text and convert it to a pdf file?I wrote a little text and named it test.tex ,and then I wrote on terminal something like latex_test.tex but it does nothing.
Could you please give me any advise?

---

### Post by mkoehler on 2008-02-20
To convert a LaTeX file to a PDF doc, you have to run a few commands.  First, make sure you have the necessary packages installed:

```
sudo apt-get install texlive-latex-base texlive-latex-extra texlive-latex-recommended
```

Next, browse to the directory where your .tex file resides, then run the following commands

```
latex <filename>.tex
dvips -o <filename>.ps <filename>.dvi
ps2pdf <filename>.ps
```

After these commands finish running, you should have a PDF file.  As for the question of what to use for writing mathematical formulas on a computer, LaTeX is the only way to go.  For example, I'll translate your equation into the LaTeX format:
```
\begin{eqnarray}
\sigma = \sqrt{{\sigma (x - \bar x)^2 \over n}}
\end{eqnarray}
```

I use LaTeX exclusively for all of my technical reports.  It creates professional looking documents, is easy to use (once you get over the learning curve), and you can use any text editor that you'd like.  I hope this helps.

---

### Post by sofos on 2008-02-20
thanks a lot,you are god
:)

---

### Post by NikoC on 2008-02-20
Here on my MacBook at work, I'm running Latex equation editor which allows you to generate and import equations to word (e.g.). Apparently there is a similar piece of software for linux found at [http://rlehy.free.fr/]("http://rlehy.free.fr/"). You still need to install latex though!

---

### Post by radiocognition on 2008-02-20
> **NikoC said:**
> Here on my MacBook at work, I'm running Latex equation editor which allows you to generate and import equations to word (e.g.). Apparently there is a similar piece of software for linux found at [http://rlehy.free.fr/]("http://rlehy.free.fr/"). You still need to install latex though!

I highly recommend these small LaTeX editors that allow you to drag and drop your finished equations into your documents.  Often for presentations and posters, I find myself relying on this rather than a more traditional LaTeX editor like KILE

---

### Post by vanadium on 2008-02-20
With

pdflatex

you immediately convert to Latex, no need vor intermediate postscript files. pdflatex also conveniently allows you to use PDF files for graphics.

Indeed, Latex is the only option for top quality, professional typesetting of documents and of mathematical formulas in particular. However, as others have posted here, OOo's math function is quite adequate in rendering formulas.

---


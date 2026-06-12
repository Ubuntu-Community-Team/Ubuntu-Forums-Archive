---
title: "Images in TeX Documents"
date: 2007-06-11
forum: Art &amp; Design
---

### Post by csevcik on 2007-06-11
I am a beginner user of TeX. I can successfully export OpenOffice documents to TeX format. But I cannot insert graphics into the exported document. I have used Kile and its graphic wizard to do this in my documents, this results in the following insertion into the document:

\begin{center}
 \includegraphics[width=7cm,bb=0 0 558 828]{Figure1.png}
 % Figure1.png: 1551x2300 pixel, 200dpi, 19.70x29.21 cm, bb=0 0 558 828
\end{center}

(the  png format may be replaced by jpg, eps etc. this does not make any difference as far as my problem is concerned) but the compiolation into a dvi file always fails with a message like:

./Sevcik_HumanIgG_figs.tex:563:Undefined control sequence. \includegraphics

(563 is the number of the line containing the \includegraphics instruction).

As far as I can see the instruction is OK. The problem occurs disregarding that tetex or livetex are installed in my machine. Documents which compile OK in a Mac with OS X fail under Ubuntu or Kubuntu 7.04. The problem is the same if I attempt to compile the document from a command line in a terminal window using the 

latex document_name

command.  Thus I guess there is something wrong with the latex command in ubuntu/kubuntu

Can somebody help?

---

### Post by God Of Atheism on 2007-06-12
You do have \usepackage{graphicx}, don't you?

---

### Post by Aelfric5578 on 2007-06-14
It sounds as though God of Atheism is right.  In order to use the command \include image you have to make sure that the line ```
\usepackage{graphicx}
``` appears at the beginning of your LaTeX source file.

I realize this isn't the cause of your problem, but I was under the impression that you needed to convert any graphics you wanted to use in LaTeX into encapsulated postscript format first.  Assuming all you're missing is that package statement, you may find that you'll still have problems using a .PNG file for your image.

---

### Post by Hasen_A on 2007-07-18
I seem to have a similar problem. When my file.tex is build with quickbild it finishes with no problems. I receive my file.dvi, but it doesn't display the graphic for the following code in my file.tex
```
\begin{figure}[ht]
		\centering	
		\includegraphics[width=1\textwidth]{test2.eps}
	\end{figure}	
```
the PDFLatex button returns the following error in the kile log:

```
[PDFLaTeX] test.tex => test.pdf (pdflatex)
[PDFLaTeX] finished with exit status 1
./test.tex:88:Unknown graphics extension: .eps. ...ludegraphics[width=1\textwidth]{test2.eps}
./test.tex:0: Label(s) may have changed. Rerun to get cross-references right.
[PDFLaTeX] 1 error, 1 warning, 0 badboxes
```

Any hints? I had no luck on google what so ever.

---

### Post by God Of Atheism on 2007-07-19
> **Hasen_A said:**
> I seem to have a similar problem. When my file.tex is build with quickbild it finishes with no problems. I receive my file.dvi, but it doesn't display the graphic for the following code in my file.tex
```
\begin{figure}[ht]
		\centering	
		\includegraphics[width=1\textwidth]{test2.eps}
	\end{figure}	
```
the PDFLatex button returns the following error in the kile log:

```
[PDFLaTeX] test.tex => test.pdf (pdflatex)
[PDFLaTeX] finished with exit status 1
./test.tex:88:Unknown graphics extension: .eps. ...ludegraphics[width=1\textwidth]{test2.eps}
./test.tex:0: Label(s) may have changed. Rerun to get cross-references right.
[PDFLaTeX] 1 error, 1 warning, 0 badboxes
```

Any hints? I had no luck on google what so ever.

Just out of curiosity (since what you wrote looked okay), I ran some old lab report again just to run into the same problem as you did. But then, since I knew I did manage to get something in the past, I tried some more things, since I knew some things depend on what type of output you use (dvi/pdf/ps). It turns out that in order to use eps graphics in your document you need to use postscript output.So:

1. make the dvi file (this will likely give quite a few error messages): run latex
2. if necessary rerun step 1 in order to get references right
3. make the postscript file: run dvips
4. (optional) view the postscript output
if you want to obtain a pdf file, then add
5. make the pdf file: run ps2pdf
6. (optional) view the pdf output

---

### Post by Bram001 on 2007-07-19
If you want to run pdflatex you could also:
1. run 'ps2pdf test2.eps test2.pdf'
2. remove the '.eps' extension in the \includegraphics command
3. run pdflatex

latex will automatically use the .eps file and pdflatex the .pdf

you can learn most of the basics for writing latex on [http://www.andy-roberts.net/misc/latex/]("http://www.andy-roberts.net/misc/latex/")

---

### Post by Hasen_A on 2007-07-19
> **Bram001 said:**
> If you want to run pdflatex you could also:
1. run 'ps2pdf test2.eps test2.pdf'
2. remove the '.eps' extension in the \includegraphics command
3. run pdflatex

latex will automatically use the .eps file and pdflatex the .pdf

you can learn most of the basics for writing latex on [http://www.andy-roberts.net/misc/latex/]("http://www.andy-roberts.net/misc/latex/")

Thanks for the tip, but I think this would create a mere single pdf for the picture and not a complete file with texts? anyhow Ive tried the other remarks above and it works. the resulting pdf just looks a bit different compared to when i compile the .tex at work with the windows version technix.

---

### Post by frisket on 2007-08-13
> **Aelfric5578 said:**
> It sounds as though God of Atheism is right.  In order to use the command \include image you have to make sure that the line ```
\usepackage{graphicx}
``` appears at the beginning of your LaTeX source file.

I realize this isn't the cause of your problem, but I was under the impression that you needed to convert any graphics you wanted to use in LaTeX into encapsulated postscript format first.  Assuming all you're missing is that package statement, you may find that you'll still have problems using a .PNG file for your image.

No, please read some documentation, eg [http://research.silmaril.ie/latex/chapter6.html#images](http://research.silmaril.ie/latex/chapter6.html#images)

EPS files only work with standard LaTeX + dvips; if you're using standard LaTeX + dvips, you MUST use EPS.

If you're using pdflatex, you must use JPG, PNG, or PDF images; if you have those formats of image, you can only use pdflatex.

---


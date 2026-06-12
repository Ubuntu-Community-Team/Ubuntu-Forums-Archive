---
title: "compiling tex documents with texlive &amp; kile"
date: 2006-11-09
forum: Absolute Beginner Talk
---

### Post by col_b on 2006-11-09
OK. I need a bit of help on this one...

I installed ubuntu the other day.  Everything is sweet.

I use latex and texnic center in windows, so I'm trying to install latex in ubuntu.  I found a few tutorials and used Synaptic to install texlive and Kile.  texlive is installed and seems to be working, i.e. it displays version info when i type tex -version.

Now, I'm trying to use kile to compile a .tex document, which I know is coded correctly.  But, I get loads of undefined control sequences when i run tex, and the .dvi output is messed up.  Does kile need configured or something?

I appreciate your help.
Cheers,
Col

---

### Post by col_b on 2006-11-09
*bump*

---

### Post by celsofaf on 2006-12-09
I have exactly the same problem, even when I try to compile via the command line! I will even uninstall TeXLive and put TeTeX to see if it somehow works!

---

### Post by David_T on 2006-12-09
Have you tried a command line from your terminal like latex myfile.tex ?

If that doesn't work, could you try a basic test example like 
```

\documentclass{article}
\begin{document}
\Huge
\emph{Hello World}
\end{document}

```
and post what kind of errors you get?

---

### Post by chalex on 2006-12-09
I remember last time I installed Kile on Ubuntu (about a year ago), there was a bunch of functionality that depended on other packages, but they weren't automatically installed because they're not required for Kile to run.  Off the top of my head, various tetex-* packages, kpdf, kdvi.

Try installing all the packages that kile Suggests: and Recommends: [http://packages.ubuntu.com/edgy/tex/kile](http://packages.ubuntu.com/edgy/tex/kile)

---

### Post by celsofaf on 2006-12-10
> **David_T said:**
> Have you tried a command line from your terminal like latex myfile.tex ?

If that doesn't work, could you try a basic test example like 
```

\documentclass{article}
\begin{document}
\Huge
\emph{Hello World}
\end{document}

```
and post what kind of errors you get?
No errors on this small test document. The DVI was generated correctly. What I don't get is: I have a document, which I know is "right" - because I compiled it last week on another computer - and compiling here gives many nonsense errors. I even have tetex-base, tetex-extra installed. :(

I'll have a closer look at it now...

---

### Post by celsofaf on 2006-12-10
OK, OK... Part of it was **my fault**. I had the .tex file saved with wrong encoding. Now it works.

Sorry for the trouble!...

---


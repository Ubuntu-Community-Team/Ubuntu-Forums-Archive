---
title: "Bibtex Help"
date: 2008-01-30
forum: Absolute Beginner Talk
---

### Post by mluxton on 2008-01-30
Hi-
I am having trouble with Bibtex.  I can get everything to compile and so on but the end of the bibliography contains a little rectangle on the end.  Any idea on how to remove this?

---

### Post by jan quark on 2008-01-31
does this rectangle perhaps belong to the text?

or do you always get this small sign in every document you open?

---

### Post by mluxton on 2008-01-31
It appears every time I run it.  If it helps, this is what produced the attached pdf:

@BOOK{H,                                                                  This of course is the bib file
  author = "R. Hartshorne",
  title = "Algebraic {G}eometry",
  publisher = "Springer-Verlag",
  series = "Graduate Text in Mathematics",
  number = "52",
  year = "1977",
  }

\documentclass{article}                                                                 Here is my tex file
\usepackage{amsfonts, amscd, amsthm, amssymb, amsmath}

\begin{document}

\bibliographystyle{amsplain}
\bibliography{1}

\cite{*}

\end{document}

---

### Post by mali2297 on 2008-01-31
The [] comes from
```

\cite{*}

```
Replace it with \cite{H} to cite the reference in the bib file.

---

### Post by mluxton on 2008-01-31
When I change \cite{*} to \cite{H}, the [] changes to [H].  Is there a command that allows my bibliography to list every source in my bib file?  It seems that without \cite{*}, the only sources that appear in my bibliography are those which are cited in the text.

---

### Post by mali2297 on 2008-01-31
> **mluxton said:**
> Is there a command that allows my bibliography to list every source in my bib file? 

Put
```

\nocite{*}

```
before
```

\bibliographystyle{amsplain}
\bibliography{1}

```

---

### Post by mluxton on 2008-01-31
That fixed it.  Thanks very much for the help!

---


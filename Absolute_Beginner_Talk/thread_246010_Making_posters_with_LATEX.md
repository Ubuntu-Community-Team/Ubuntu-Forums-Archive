---
title: "Making posters with LATEX"
date: 2006-08-28
forum: Absolute Beginner Talk
---

### Post by aam-aadmi on 2006-08-28
I am trying to make a poster (for a presentation at a conference) using Latex. I am trying to use the following example:
[http://nxg.me.uk/docs/posters/poster-template-portrait.tex](http://nxg.me.uk/docs/posters/poster-template-portrait.tex)

to get started.

But, when I try to compiple the above file with
```
latex poster-template-portrait.tex
```

I get the following error message:
[HTML]! LaTeX Error: File `a0poster.cls' not found.[/HTML]

I think I need to install a few packages, but I don't know which ones. Does any one have any ideas?

Thanks.

---

### Post by IYY on 2006-08-28
Quoting from the URL you provided:

> In outline, you use the a0poster class (browse, zip) to handle the page size and fonts for an A0 plotter, and the textpos package (browse, zip)to place text at arbitrary positions on the page.

The packages are here: [http://www.tex.ac.uk/tex-archive/macros/latex/contrib/a0poster.zip](http://www.tex.ac.uk/tex-archive/macros/latex/contrib/a0poster.zip)
and here: [http://www.tex.ac.uk/tex-archive/macros/latex/contrib/textpos.zip](http://www.tex.ac.uk/tex-archive/macros/latex/contrib/textpos.zip)

---


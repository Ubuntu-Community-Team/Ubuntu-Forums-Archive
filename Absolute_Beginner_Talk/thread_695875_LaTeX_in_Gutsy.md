---
title: "LaTeX in Gutsy?"
date: 2008-02-13
forum: Absolute Beginner Talk
---

### Post by spacefreak86 on 2008-02-13
I'm trying  to figure out how to get LaTeX, GSView, Ghostscript, and the actual TeX system on Ubuntu 7.10 (Gutsy). Right now I'm having to use Windows TeXnicCenter and MikTeX on Windows for compiling, though I did find a cool program with a nice interface by the name of TeXMaker that seems similar to TeXnicCenter. I tried finding GSView and Ghostscript on sourceforge, but could only find the tar.gz files for it, to which I dont' know how to use yet.

I also need to find the actual TeX language and libraries to use with TeXMaker, as well as figure out how to set it so that it creates .pdf files (preferably with the click of a few buttons). Anyone know how to go about this?

---

### Post by mali2297 on 2008-02-13
> **spacefreak86 said:**
> I tried finding GSView and Ghostscript on sourceforge, but could only find the tar.gz files for it, to which I dont' know how to use yet.

Why not use the default document viewer **evince**? If you want a lighter alternative, try **xpdf**.

> I also need to find the actual TeX language and libraries to use with TeXMaker

Install the package **texlive-latex-recommended** with all of its dependencies. Use Synaptic.

---

### Post by macogw on 2008-02-13
I'd install texlive-latex-extra since it includes lots more packages/classes which come in handy (like the MLA one for school, or the resume one).  It'll automatically pull in texlive-latex-recommended and -base and -common and everything.

---

### Post by spacefreak86 on 2008-02-13
I did not know about evince, but I will look for it. Do you know if there is any special configuration to get it to work?

---

### Post by mali2297 on 2008-02-13
> **spacefreak86 said:**
> I did not know about evince, but I will look for it. Do you know if there is any special configuration to get it to work?

It should be rather straight-forward.
[https://help.ubuntu.com/community/Evince](https://help.ubuntu.com/community/Evince)

---

### Post by spacefreak86 on 2008-02-14
I got it, I just had to change it so that the pdf viewer was set to adobe acrobat. Awesomeness!

---


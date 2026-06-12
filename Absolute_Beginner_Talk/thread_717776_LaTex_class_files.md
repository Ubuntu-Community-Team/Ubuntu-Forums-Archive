---
title: "LaTex class files"
date: 2008-03-07
forum: Absolute Beginner Talk
---

### Post by islandxlb on 2008-03-07
I just installed Texlive on Ubuntu and find that I need to install new class files.  I am not sure where to put these files and whether there are any other operations I need to perform to get Tex to recognize them.  

I have the class file in the same directory as my .tex file but when I try to "latex filename.tex" I get errors indicating that Tex can't find the class file.  So, I think there must be somewhere else I'm supposed to put the thing.

Any help would be appreciated, including pointers to appropriate online documentation.  Thanks!

---

### Post by euclid6609 on 2008-03-07
On most systems you can put class files into any place below /usr/share/texmf/tex/latex/, perhaps in a new directory for your own class files. They must be named something.cls and referred to like \documentclass[options]{something} (without the extension). This should also work if you have the class file locally in the same directory where you run LaTeX. (Just to confirm - you are not talking about style files(something.sty)? They go in the same place, but you need to run texhash for LaTeX to find them).

---

### Post by frisket on 2008-03-20
> **islandxlb said:**
> I just installed Texlive on Ubuntu and find that I need to install new class files.  I am not sure where to put these files and whether there are any other operations I need to perform to get Tex to recognize them.  

I have the class file in the same directory as my .tex file but when I try to "latex filename.tex" I get errors indicating that Tex can't find the class file.  So, I think there must be somewhere else I'm supposed to put the thing.

Any help would be appreciated, including pointers to appropriate online documentation.  Thanks!

[http://latex.silmaril.ie/formattinginformation/chapter5.html#where](http://latex.silmaril.ie/formattinginformation/chapter5.html#where)

P

---


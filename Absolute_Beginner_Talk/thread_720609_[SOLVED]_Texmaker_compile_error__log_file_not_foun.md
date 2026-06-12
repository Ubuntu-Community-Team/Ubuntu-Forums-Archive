---
title: "[SOLVED] Texmaker compile error : log file not found"
date: 2008-03-10
forum: Absolute Beginner Talk
---

### Post by amyst on 2008-03-10
I used Synaptic and download texmaker 1.6. Upon compilation of any .tex file, I get an error message in a dialog box:

 log file not found

I searched the forum, web, launchpad, and  the only suggestion I found is to save an uncompiled latex file as .tex, and then compile it. Some people reported that this method solves the log file error, but it doesn't  in my case.

Did I forget to set the correct paths to tex packages? I haven't configure texmaker since I obtained it from Synaptic. Advice appreciated!

---

### Post by amyst on 2008-03-11
Wow I am stupid - I ended up solving my own problem. The issue appear to not be in texmaker, but that I didn't download any latex packages  (texlive-latex-recommended courtesy from another thread), and texmaker misled this info by always outputting "log file not found". 

I just installed texlive-latex-recommended and texmaker works if files are explicitly saved in .tex format. I also installed beamer package but some fonts appear to be missing. Based on the helpful comments I received on kile, I am thinking of installing kile and do an interface comparison between the two editors.

I'm using kile now :)

---


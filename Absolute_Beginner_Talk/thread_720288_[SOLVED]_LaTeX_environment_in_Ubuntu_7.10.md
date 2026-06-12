---
title: "[SOLVED] LaTeX environment in Ubuntu 7.10?"
date: 2008-03-10
forum: Absolute Beginner Talk
---

### Post by Ryozanpaku Tiger on 2008-03-10
Dear all,

I would like to have a LaTeX environment in my Ubuntu 7.10. I have used MikTeX under Win XP.

Is there any good instruction on how to set up LaTeX under Ubuntu, including comparison of versions, front-ends, etc.? What is the difference between teteX and TeX Live?

Thank you!

---

### Post by ansicplusplus on 2008-03-10
Hy,
you should stick to TeX-Live since tetex is no longer developed upstream. I prefer Kile as frontend. There is no need for a largescale setup as on windows. If you have no absolutely special demands it will just work.
Happy texing, ansicplusplus

---

### Post by tyle on 2008-03-10
I have used Kile for a few months when writing LaTeX, and have no complaints so far.

---

### Post by sotiriss on 2008-03-10
I use KIle too. I am satisfied with kile.

---

### Post by mali2297 on 2008-03-10
Install the package **texlive-latex-recommended** with its dependencies, and perhaps some additional packages (search latex in Synaptic).

For an editor, I personally use Emacs with AUCTeX.

---

### Post by Ryozanpaku Tiger on 2008-03-10
Thank you very much, guys! I will install Tex Live. As about front-end, as far as I know, Kile is valid for KDE. But I use GNOME. Actually I am new to Ubuntu, but I like GNOME desktop and see no reason for change to KDE. Which front-end is good for GNOME? Thank you!

---

### Post by Stevko on 2008-03-10
There is an editor called Winefish that is for Gnome/GTK+ and for LaTeX. You can try it.

---

### Post by Ryozanpaku Tiger on 2008-03-10
But will Kile run under Gnome or not?

---

### Post by Whiffle on 2008-03-10
Yep it will, and thats what I would do if I were using gnome.

---

### Post by ansicplusplus on 2008-03-10
Hy,
I use Kile with Gnome, too. It works just fine. There ist just one difficulty I remember. If it doesn't launch a PDF-Viewer and instead too short error messages, simply install kpdf. I guess the default ist configured to use kpdf and fails miserably if it's missing.

Yours, ansicplusplus.

---

### Post by Whiffle on 2008-03-10
you can change the pdf viewer by going to settings > Configure Kile > Tools Build and then changing programs there.

Also, kile has a built in system checker that will make sure all the tools you need are installed.  Settings > System Check

---

### Post by Tantor on 2008-03-12
I have also migrated from WinXP - Miktex - WinEdt to Ubuntu - Texlive - Kile and I am very satisfied. However, there are a couple of small things I can't get to work properly. Maybe someone can give me some advice.

(1) I have reconfigured Kile so that the default DVI/PDF viewer is evince. If I quickbuild (i.e. complie and preview) a tex file and then do some changes to the tex source and rebuild, the viewer (evince) updates the file but returns to the very beginning of the document so I have to scroll down to where I was to continue editing. Any workaround?

(2) Miktex, when my tex file needed some latex package to compile, automatically connected to the internet and downloaded it. Is there some similar functionality in the free world? In Synaptics I sometimes find some "global" packages containing a lot of individual packages but I haven't found a way to install a single package from a repository.

(3) No inline spell checker. I know this is going to be address in future versions of KDE. It is a bit of a problem because when I do a regular spell check I get a lot of errors from portions of my code that I would never have had scanned (like commands I have defined, etc.). With an inline checker I just pay attention to the errors I care of.

I hope that someone has some suggestions!

---


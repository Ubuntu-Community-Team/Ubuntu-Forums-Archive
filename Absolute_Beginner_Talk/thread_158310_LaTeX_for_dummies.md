---
title: "LaTeX for dummies"
date: 2006-04-10
forum: Absolute Beginner Talk
---

### Post by Impydimp on 2006-04-10
Ok, so I want to install LaTeX as well as make my emacs editor help me out viz generating .ps and/or .pdf (I used to use WinEdt but now I am making the change to Linux so I am trying to emulate this type of editor as much as possible).

I have gone to the synaptic package manager and downloaded all the files that it tells me to (and I have checked these are correct by looking at forum posts).

BUT, I can't make it work! I can find the files but every time I try to run the executables nothing happens. Can someone please give me a hint as to how I can actually use the programmes? 

hope this makes sense

---

### Post by taurus on 2006-04-10
What executables are we talking here?  I think you should also install lyx if you want to use TeX or LaTeX...

---

### Post by aam-aadmi on 2006-04-10
Once you have installed Tetex (the version of Latex that is avilable in Ubuntu); you can do the following to write and compile your documents.

1. Write your code using GEdit (you don't need EMacs; any text editor will do).

2. Save the file as filename.tex (a file with a tex extension) to some directory and note that.

3. Open the terminal and go to the directory where you saved the file (You can use cd/home/username/directoryname)

4. You can now compile your  document as follows:

latex filename.tex
latex filename.tex
xdvi filename.dvi
dvips -o filename.ps filename.dvi

OR

pdflatex filename.tex
acroread filename.pdf 

(The first method gives a post-script file and the second gives a pdf; of course for the second method to work you should have installed xpdf).

---

### Post by adamkane on 2006-04-11
kile is the most user-friendly latex editor:
[http://kile.sourceforge.net/](http://kile.sourceforge.net/)

```

sudo apt-get install kile

```

---

### Post by aam-aadmi on 2006-04-11
Can kile be used in the GNOME desktop environment? Or is it meant onlu for KDE?

---

### Post by halfvolle melk on 2006-04-11
Yes, but it will install some more KDE stuff it depends upon. Other than that it works fine under Gnome.

---

### Post by Impydimp on 2006-04-15
Thanks a lot you guys.  aam-aadi - you're advise was just what I needed - cheers!

---


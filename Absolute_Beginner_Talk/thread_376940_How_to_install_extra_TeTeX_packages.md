---
title: "How to install extra TeTeX packages?"
date: 2007-03-05
forum: Absolute Beginner Talk
---

### Post by mahy on 2007-03-05
Hi y'all

i just downloaded the cjhebrew.zip TeTeX package and i can't figure out what to do with it. Can somebody tell me exactly what should i do? THX for any help.

---

### Post by peabody on 2007-03-05
Where did you download it from?  Were you sure it wasn't in the Ubuntu repositories?

I'm no (La)TeX expert, but from my understanding you should just be able to unzip the contents to a folder, and compose your .tex file in there.  Just remember to put the \usepackage{whatever_this_package_is_called.sty} in your document.

---

### Post by peabody on 2007-03-05
Found this in the short guide to latex:

4.6 Installing Extra Packages

Most LATEX installations come with a large set of pre-installed style packages,
but many more are available on the net. The main place to look for style
packages on the Internet is CTAN ([http://www.ctan.org/)](http://www.ctan.org/)).
Packages such as geometry, hyphenat, and many others are typically
made up of two files: a file with the extension .ins and another with the
extension .dtx. There will often be a readme.txt with a brief description
of the package. You should of course read this file first.
In any event, once you have copied the package files onto your machine,
you still have to process them in a way that (a) tells your TEX distribution
about the new style package and (b) gives you the documentation. Here’s
how you do the first part:
1. Run LATEX on the .ins file. This will extract a .sty file.
2. Move the .sty file to a place where your distribution can find it. Usually
this is in your .../localtexmf/tex/latex subdirectory (Windows
or OS/2 users should feel free to change the direction of the
slashes).
4.7 Working with pdfLATEX 79
3. Refresh your distribution’s file-name database. The command depends
on the LATEXdistribution you use: teTeX, fpTeX – texhash; web2c –
maktexlsr; MikTeX – initexmf -update-fndb or use the GUI.
Now you can extract the documentation from the .dtx file:

---

### Post by frisket on 2007-03-08
See the description of how and where to install packages at [http://research.silmaril.ie/latex/chapter5.html#pkginst](http://research.silmaril.ie/latex/chapter5.html#pkginst)

---

### Post by yigal.weinstein on 2007-03-09
mahy,

I know this is not directly answering your post, but if you are using a lot of extra packages in the tetex distribution you may want to consider installing texlive instead of tetex.  It contains all current packages on CTAN etc..

Also after putting the .sty files with the .sty and the .cls files with .cls files etc. all you need to do for both texlive and tetex is run,

```
sudo texhash
```

best.

---


---
title: "LaTeX (Resolution)"
date: 2006-01-18
forum: Absolute Beginner Talk
---

### Post by amcavoy on 2006-01-18
I have installed the following:

tetex-base
tetex-bin
tetex-extra
latex-ucs

Now I am able to use the 'pdflatex' command to turn my TeX files into PDF files.  However, the resolution seems to be low.  How might I go about changing it?

Thank you.

---

### Post by paulmilliken on 2006-01-18
[QUOTE=amcavoy]I have installed the following:

tetex-base
tetex-bin
tetex-extra
latex-ucs

Now I am able to use the 'pdflatex' command to turn my TeX files into PDF files.  However, the resolution seems to be low.  How might I go about changing it?

Thank you.[/QUOTE]
I do it a slightly different way.  Say I have a file called example.tex.  I compile it with:
"latex example.tex".
Then I convert the dvi file to a pdf file with:
"dvipdfm -o example.pdf example.dvi".

---

### Post by WhizCas on 2006-01-19
[quote=paulmilliken]I do it a slightly different way.  Say I have a file called example.tex.  I compile it with:
"latex example.tex".
Then I convert the dvi file to a pdf file with:
"dvipdfm -o example.pdf example.dvi".[/quote]

This shouldnt make any difference.

Sometimes when you view a pdf the resolution stays low for sometime, try not to scroll and wait. Or try another pdf viewer maybe?

---

### Post by amcavoy on 2006-01-19
Actually, the steps paulmilliken suggested worked fine; that method gives me high-res PDF's.  I was looking for a way that I could make this happen with 'pdflatex' but for my purposes, his way will work quite well.

Thank you!

---

### Post by mirna on 2006-01-28
Hi,

I tried installing latex starting with:
apt-get install tetex-base

The message that I get is:
The following packages have unmet dependencies:
  tetex-base: Depends: texinfo (>= 4.0b-1) but it is not going to be installed

I have no idea what texinfo is and since I am new to linux I ran
apt-get install texinfo

and I get

Reading package lists... Done
Building dependency tree... Done

Then I do again:
apt-get install tetex-base

and I get the same thing:
The following packages have unmet dependencies:
  tetex-base: Depends: texinfo (>= 4.0b-1) but it is not going to be installed

So obvously I didn't install  texinfo, or ???. What is interesting is that I installed emacs with tetex-base and tetex-extra, and ...   on a different machine that is also running ubuntu 5.04.
I would be very grateful for help on this, because as it is I am stuck!

Mirna
Also, does anyone know how to start a thread on this forum???

---

### Post by mirna on 2006-01-28
The problem was:
I needed to run apt-get -f update, and then it was fine.

Mirna

---


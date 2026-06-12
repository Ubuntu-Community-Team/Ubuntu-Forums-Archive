---
title: "[SOLVED] Delete text from every page of a pdf document"
date: 2008-01-29
forum: Absolute Beginner Talk
---

### Post by u-slayer on 2008-01-29
Hi everyone.

I am trying to use pdfedit, to search for and delete a block of text from every page of a pdf file. I can manage to do this manually, but the document is over 300 pages long. I also tried drawing a rectangle over the text, but it always comes out black and I still don't know how to apply it to every page. Does anyone know how to use pdfedit's internal command line to automate this task? 

thanks

---

### Post by Paulmd on 2008-01-29
> **u-slayer said:**
> Hi everyone.

I am trying to use pdfedit, to search for and delete a block of text from every page of a pdf file. I can manage to do this manually, but the document is over 300 pages long. I also tried drawing a rectangle over the text, but it always comes out black and I still don't know how to apply it to every page. Does anyone know how to use pdfedit's internal command line to automate this task? 

thanks

If it's the same text, you can do a search and replace.

For example Search for "the quick brown fox" replace with " " (a space)

If the texts in the blocks are dissimilar, I'm not sure.

---

### Post by u-slayer on 2008-01-30
> **Paulmd said:**
> If it's the same text, you can do a search and replace.

For example Search for "the quick brown fox" replace with " " (a space)

If the texts in the blocks are dissimilar, I'm not sure.

This is exactly what I want to do. However, the only program that I know of that can edit pdf files, pdfedit,
[LIST=1]
[*]Only has a Search, not a replace function.
[*]Can't search over multiple pages
[/LIST]

If you know something I don't, like a better program to edit pdf files or a command line trick inside pdfedit, please let me know, thanks.

---

### Post by Paulmd on 2008-01-30
> **u-slayer said:**
> This is exactly what I want to do. However, the only program that I know of that can edit pdf files, pdfedit,
[LIST=1]
[*]Only has a Search, not a replace function.
[*]Can't search over multiple pages
[/LIST]

If you know something I don't, like a better program to edit pdf files or a command line trick inside pdfedit, please let me know, thanks.

koffice can import pdfs.

PS:
If you have a Windows machine, there is a 30 day trial of Acrobat professional. The blurb says the trial is fully functional. It should get you past that one big document. 

[http://www.adobe.com/products/acrobatpro/tryout.html](http://www.adobe.com/products/acrobatpro/tryout.html)

This is a PS 'cuz it's a non-linux solution.

---

### Post by u-slayer on 2008-01-31
> **Paulmd said:**
> koffice can import pdfs.


Okay I downloaded koffice. 

Koffice workspace said "missing export filter"
kword imported the pdf but failed to render most of the symbols and destroyed the formatting of the document.

All i need to do is chop an inch off of the bottom of the document. Isn't there anything that can do this?

---

### Post by u-slayer on 2008-02-22
I found a solution.  I used pdfcrop to crop the text off the bottom of every page. I got it from a package called texlive-extra-utils

---


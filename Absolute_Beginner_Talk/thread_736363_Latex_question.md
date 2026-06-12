---
title: "Latex question"
date: 2008-03-26
forum: Absolute Beginner Talk
---

### Post by chs773 on 2008-03-26
So i am new to unbuntu and I am trying to figure out how i could write latex files in unbuntu.

what would i need to download to do this?

thanks

---

### Post by Bachstelze on 2008-03-26
A text editor :)

Or did you mean *compile* them? See [here](https://help.ubuntu.com/community/LaTeX).

---

### Post by chs773 on 2008-03-28
okay so i type my latex file in the text editor and save it as a .tex file right

so what do i need to download to compile it?

and what do i type in the terminal window to compile it?

thanks

---

### Post by Bachstelze on 2008-03-28
See the link ;)

---

### Post by nike984 on 2008-03-28
install 'texlive-full' package in the synaptic
then install 'kile' , 'texmaker' , and 'lyx'.

After then that you can use kile or texmaker or lyx to
edit tex file. 
My choice is definitely 'kile' .
It's the best LaTex editor IMHM.

---

### Post by Bachstelze on 2008-03-28
> **nike984 said:**
> 
My choice is definitely 'kile' .
It's the best LaTex editor IMHM.

Agreed. Can't be otherwise since it starts with a K ;)

---

### Post by mali2297 on 2008-03-28
Install the package **texlive-latex-recommended** with its dependencies. If you want, you can also install **texlive-latex-extra**.

To directly produce a pdf file from example.tex, type
```

pdflatex example.tex

```
in the terminal.

For an editor, many recommend Kile. You can also use Emacs+AUCTeX or, say, Vim.

---

### Post by frisket on 2008-04-09
And please, Please, PLEASE read some doc before jumping in with both feet :-)
It'll make it a much more pleasant experience, and prevent you picking up all sorts
of bad habits from people who learned their LaTeX 20 years ago.

[http://latex.silmaril.ie/formattinginformation/](http://latex.silmaril.ie/formattinginformation/)

///Peter

---


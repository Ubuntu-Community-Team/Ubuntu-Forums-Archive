---
title: "Concatenting output from two or more print jobs to PDF printer"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by tjod on 2007-03-11
Hi;

I'm currently using CUPS PDF printer in Ubuntu 6.10. Works fine for most things, but I'm trying to figure out how to print multiple print jobs to one PDF file.:confused: 

e.g. If I am trying to print multiple pages from a website but have them show up sequentially in one PDF fie, how would I o about that? 

Can PDF files simply be added like 1.PDF+2. PDF > 3.PDF  like text files? Or do I need a different version of the PDF printer application?

Thanks!

Tim O

---

### Post by chewearn on 2007-03-12
I use pdftk to join multiple pdf files into one, like this:
```
pdftk inputfile1.pdf inputfile2.pdf inputfile3.pdf cat output outputfile.pdf
```
You can find pdftk in the universe repo.

---

### Post by mlissner on 2007-03-12
Hey - I saw this post earlier today, and I did a bit of research. If you do an apt-get install pdftk, it has a feature that will allow you to join two (or more) pdf files together. 

Once it's installed, if you do this:
```
 pdftk in1.pdf in2.pdf cat output out1.pdf
```

It will join in1.pdf with in2.pdf, creating a third pdf called out1.pdf. It's an extra step that you'd have to take, but it looks promising. You might check out its man page as well. That's where the above command comes from.

---

### Post by mlissner on 2007-03-12
> **AstalaVista said:**
> I use pdftk to join multiple pdf files into one, like this:
```
pdftk inputfile1.pdf inputfile2.pdf inputfile3.pdf cat output outputfile.pdf
```
You can find pdftk in the universe repo.

Wow. You beat me to the punch! Jeesh. Sometimes I wonder if I should post at all (j/k).

---

### Post by chewearn on 2007-03-12
> **mlissner said:**
> Wow. You beat me to the punch! Jeesh. Sometimes I wonder if I should post at all (j/k).

Sorry, I was checking unanswered posts.  This one was 10 hour old when I replied, so I didn't think there was a race for an answer.  :biggrin:

---

### Post by tjod on 2007-03-12
Thanks, all! 

 pdftk works great. 8-)

Tim O

---


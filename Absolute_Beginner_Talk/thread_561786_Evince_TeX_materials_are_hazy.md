---
title: "Evince: TeX materials are hazy"
date: 2007-09-28
forum: Absolute Beginner Talk
---

### Post by sauravbhaumik on 2007-09-28
I'm using 0.8.1 version and whenever I open up a mathematics text, the mathematical notations come hazy. 
The other things are quite clear, but only the mathematical part which is necessarily TeXed, come hazy.
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=44606&stc=1&d=1190953926[/IMG]
In the above image, you may see what kind of proble is there with the TeX material.
Kindly help.


Though it is not seen in ALL the mathematical texts, but it is seen in MOST of the mathematical texts.

---

### Post by finer recliner on 2007-09-28
try exporting to postscript or pdf...any difference?

---

### Post by stchman on 2007-09-28
Use Acrobat for your .pdf viewing.  Acrobat looks far better.

Use my procedure here to install Acrobat 7.

[http://www.stchman.com/install_adobe.html](http://www.stchman.com/install_adobe.html)

---

### Post by qamelian on 2007-09-28
> **stchman said:**
> Use Acrobat for your .pdf viewing.  Acrobat looks far better.


Acrobat doesn't look any better on either my laptop or my desktop. Until the release of the new Evince in Gnome 2.20, the only reason I can find for using Acrobat is fillable 
forms. The new Evince will supposedly handle them, so I won't be needing Acrobat at all.

---

### Post by stchman on 2007-09-28
> **qamelian said:**
> Acrobat doesn't look any better on either my laptop or my desktop. Until the release of the new Evince in Gnome 2.20, the only reason I can find for using Acrobat is fillable 
forms. The new Evince will supposedly handle them, so I won't be needing Acrobat at all.

PDFs look way better using Acrobat that Evince IMO.  It is also far easier to print with Acrobat.  I know Acrobat is not open source but it works the best.

---

### Post by bruce89 on 2007-09-28
Use pdfLaTeX instead of TeX to create a PDF:

```
pdftex file.tex
```

> **stchman said:**
> It is also far easier to print with Acrobat.

Don't know where you get that from.

It would be useful if you gave us a copy of the original LaTeX file. How did you generate the PDF, was it LaTeX -> DVI -> PS -> PDF?

Here's what pdfLaTeX does for me [ATTACH]44646[/ATTACH]

---

### Post by sauravbhaumik on 2007-09-29
> **stchman said:**
> Use Acrobat for your .pdf viewing.  Acrobat looks far better.

Use my procedure here to install Acrobat 7.

[http://www.stchman.com/install_adobe.html](http://www.stchman.com/install_adobe.html)

Acrobat seems to have solved my problem; but I don't know how it would behave while printing. Thanks, mate :). However, in the add-remove I didn't see the Acrobat, but in automatix it is there. Why is the difference?

---

### Post by stchman on 2007-10-02
> **sauravbhaumik said:**
> Acrobat seems to have solved my problem; but I don't know how it would behave while printing. Thanks, mate :). However, in the add-remove I didn't see the Acrobat, but in automatix it is there. Why is the difference?

Acrobat was removed from the repositories for Feisty.  I don't know why but it is.  It is in the Medibuntu repositories.  I would avoid using Automatix as I have read it is a lot of trouble.

---


---
title: "[SOLVED] Open Office"
date: 2007-11-27
forum: Absolute Beginner Talk
---

### Post by CryptiniteDemon on 2007-11-27
Hey, all.

Here's an odd one.  Whenever I export a document from Open Office Text editor as a PDFfor some reason it turns all of my double quotes " into spaces in the PDF.  It still remains a double quote in my original document, however.

Any idea on this?

---

### Post by stchman on 2007-11-27
> **CryptiniteDemon said:**
> Hey, all.

Here's an odd one.  Whenever I export a document from Open Office Text editor as a PDFfor some reason it turns all of my double quotes " into spaces in the PDF.  It still remains a double quote in my original document, however.

Any idea on this?

Give us an example please.

---

### Post by CryptiniteDemon on 2007-11-27
Well say I type in the following:

"Hello World"



When I export to pdf, the pdf will only display this:

 Hello World 




It simply replaces the quotes with spaces.

---

### Post by stchman on 2007-11-27
> **CryptiniteDemon said:**
> Well say I type in the following:

"Hello World"



When I export to pdf, the pdf will only display this:

 Hello World 




It simply replaces the quotes with spaces.

I will have to try that when I get home later.  One other wat to generate a .pdf is to install the cups-pdf package.

[http://www.stchman.com/pdf_cups.html](http://www.stchman.com/pdf_cups.html)

It is basically a print to pdf function.

---

### Post by asmiller-ke6seh on 2007-11-27
> **CryptiniteDemon said:**
> Well say I type in the following:

"Hello World"

When I export to pdf, the pdf will only display this:

 Hello World 

It simply replaces the quotes with spaces.

It might be a font replacement problem, with the substituted font not having quotes in the character set.

I will, however, defer to the technical experts.

---

### Post by CryptiniteDemon on 2007-11-27
> **stchman said:**
> I will have to try that when I get home later.  One other wat to generate a .pdf is to install the cups-pdf package.

[http://www.stchman.com/pdf_cups.html](http://www.stchman.com/pdf_cups.html)

It is basically a print to pdf function.

I have CUPS PDF already, but I never thought of that.  Turns out that it does print quotes just fine.  However, I can't remember if the cupsPDF allows us to have the same options as OOo export.

The reason I ask is because I'm writing up a large technical manual that I mail out to employees and I want to shrink the file size somewhat.

---

### Post by stchman on 2007-11-27
> **CryptiniteDemon said:**
> I have CUPS PDF already, but I never thought of that.  Turns out that it does print quotes just fine.  However, I can't remember if the cupsPDF allows us to have the same options as OOo export.

The reason I ask is because I'm writing up a large technical manual that I mail out to employees and I want to shrink the file size somewhat.

I don't know that either.  Once you are done making the .pdf file you can zip it to make it smaller.

---

### Post by bapoumba on 2007-11-27
Tested with "Hello world", works here for me.

---

### Post by CryptiniteDemon on 2007-11-27
Okay nevermind, I figured it out.  Whoever said it had to do with the font type was right.

My document was partially translated from another document, so OOo was giving the font the times font but gave it the name twice for some reason.  When I selected it all and then changed it to times it then would convert it.  

Odd though considering the text was already in times new roman.  

Grrr, cross platform is frustrating sometimes.

---

### Post by stchman on 2007-11-27
> **CryptiniteDemon said:**
> Okay nevermind, I figured it out.  Whoever said it had to do with the font type was right.

My document was partially translated from another document, so OOo was giving the font the times font but gave it the name twice for some reason.  When I selected it all and then changed it to times it then would convert it.  

Odd though considering the text was already in times new roman.  

Grrr, cross platform is frustrating sometimes.

If you have solved teh thread then mark thread [SOLVED] via the Thread Tools.

---


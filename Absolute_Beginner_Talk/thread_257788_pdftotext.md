---
title: "pdftotext?"
date: 2006-09-15
forum: Absolute Beginner Talk
---

### Post by jimw on 2006-09-15
Does Dapper not have pdf2text or pdf2html?  If not, does it have any other utilities that can do the same thing, that is, change pdfs to text or html?

JimW

---

### Post by jimw on 2006-09-16
> **jimw said:**
> Does Dapper not have pdf2text or pdf2html?  If not, does it have any other utilities that can do the same thing, that is, change pdfs to text or html?

JimW

'Nother one of those things.  Information said it should be part of xpdf, which I have on board.  locate couldn't find it.

However, I did find a xpdf-utils.list.

There on the list was /usr/bin/pdftotext entered that, and it started.

Once I found it, all I have to do is enter 'pdftotext' and it runs, and what's more, locate can now find it.

Can anyone explain this?

JimW

---

### Post by nsilva on 2007-12-01
Download poppler-utils

```
sudo apt-get install poppler-utils
```

It should contain pdftotext and pdftohtml

---

### Post by Majorix on 2007-12-01
My experience with pdftotext is that it cannot save the files in a format that can be viewed under Windows.
My experience with pdftohtml is that it fails to correctly extract images.

Better to keep them as .pdf.

---


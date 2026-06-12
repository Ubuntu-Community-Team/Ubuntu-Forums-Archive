---
title: "[SOLVED] Convert a PDF file"
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by theharshone on 2008-01-06
I have a pdf file i need to convert to a text file. Is there any program that can use OCR on it since it was scanned?

---

### Post by towsonu2003 on 2008-01-06
converting pdf to txt is kinda flaky but you can use pdftotext and then try to fix the layout and such... to install:

```

sudo apt-get install xpdf-utils

```

to make it work:
```

man pdftotext
pdftotext file.pdf file.txt

```

---

### Post by theharshone on 2008-01-07
Thanks! Worked perfectly

---


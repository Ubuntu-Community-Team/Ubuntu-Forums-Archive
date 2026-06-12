---
title: "Problem with chm2pdf"
date: 2008-04-14
forum: Absolute Beginner Talk
---

### Post by NawaMan on 2008-04-14
I use chm2pdf to convert a chm to a pdf. I installed libchm-bin, libchm-dev, pdftk, python-chm and htmldoc and run it. It shows a lots of text and at the end it shows:

htmldoc: /usr/local/lib/libgcc_s.so.1: version `GCC_4.2.0' not found (required by htmldoc)

It also said it write the output file. However, I do not see the output file. Is there any suggestion?

Thanks in Advance.
NawaMan

---

### Post by estaticd on 2008-04-14
This should do the trick:

sudo ln -s /lib/libgcc_s.so.1 /usr/lib/libgcc_s.so.1

Cheers.

---


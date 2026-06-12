---
title: "Tesseract OCR"
date: 2006-09-28
forum: Absolute Beginner Talk
---

### Post by webbie180 on 2006-09-28
Anyone tried?

---

### Post by webbie180 on 2006-09-29
Does this work?

---

### Post by flygin on 2006-10-27
yes, it works great!

there is just no layout detection, so create bitmap images with the right selection. Kooka can do this. Save the files and ocr them with tess...

Link to the shell scrip. It converts one or many file(s), ocrs it(them) and outputs the scanned text.

[http://www.geocities.com/thierryguy/tess_wrap.html](http://www.geocities.com/thierryguy/tess_wrap.html)

if you use 64 bit, compile it in chrooted 32 bit environment (to compile 32 bit inside 64 with the flag (-m32) option did not work in my case).

---

### Post by flygin on 2006-10-30
[http://www.geocities.com/thierryguy/tess_wrap.html](http://www.geocities.com/thierryguy/tess_wrap.html)
here the updated shellscript

---


---
title: "Open Office Calc, referencing other workbook in formula"
date: 2007-07-04
forum: Absolute Beginner Talk
---

### Post by zora123 on 2007-07-04
Hello,
I'm ubuntu newbie. I have a problem with formula in open office calc. (maybe this isnt the right forum for my question, but i'd be really glad if someone can help me).

in my formula, i want to make a reference to a cell outside of the workbook i'm working on. how could i do this in open office?

thanks in advance.

---

### Post by swisscow on 2007-07-04
Hi, just tried this so know it works

If you want to link to a cell on a different sheet, just press = then change sheet and click on the cell you want to reference to, then press return - job done.

If you want to link to a completely separate work book, this is what I did:

I opened up both work books, went to the cell I wanted to get the information from, right click - copy.
Then I went to the cell I wanted to put the information in, right click - paste special, make sure you select the checkbox labelled link. It put the following code in the cell.

```
{=DDE("soffice";"/home/dave/Desktop/test1.ods";"Sheet1.A1")}
```

In this case it has linked the cell A1, from sheet A1, in workbook test1.ods which I have placed on the desktop.

Try it!!!

---

### Post by zora123 on 2007-07-05
wow! DDE!
new thing for me.

it works perfectly. 
thanks a lot, swisscow.
:D

---

### Post by swisscow on 2007-07-05
You are most welcome! New thing for me too!

---


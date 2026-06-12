---
title: "Scanned PDF scrambled"
date: 2012-04-01
forum: Asus Ubuntu Support (CLOSED)
---

### Post by johan_olsen on 2012-04-01
Hi!
I have a Canon Pixma MP560 which has been working perfectly until last week. The printing is ok, but there has come a scanner problem. The result is the same in SimpleScan and XSane - the scanned document shows a randomly placed grayish fields,(the original on the attatchemt is a white paper with no shades) see the attachment. If I scan to a USB inserted in the printer, the result is fine, so the problem is not in the printer. I connect to the printer wireles and uses Ubuntu 11.04 - I hope sombody out there can help me find out what is wrong! I have an Asus N73J

Here is the attatchment: [https://docs.google.com/document/pub?id=1wlr5YqhatMs-yWICaf7NMrqyEsIR5uv_7DYno62otQg]("https://docs.google.com/document/pub?id=1wlr5YqhatMs-yWICaf7NMrqyEsIR5uv_7DYno62otQg")
Johan, Norway.

---

### Post by WasMeHere on 2012-04-01
Hi Johan,

What happens if you make a jpg file instead of a pdf file? This might help locating the bad encoding.

Olle

---

### Post by johan_olsen on 2012-04-01
Scanning jpg works well, but then it is impossible to scan several pages into one file. And, btw, the pdf-file produced while scanning more pages becomes corrupt and can not be opened. 

Johan

---

### Post by WasMeHere on 2012-04-01
> **johan_olsen said:**
> Scanning jpg works well, but then it is impossible to scan several pages into one file. And, btw, the pdf-file produced while scanning more pages becomes corrupt and can not be opened. 

Johan

OK, so it is the software creating or displaying pdf, that is causing the problem. Have you checked that you can display other pdf files with several pages without problems?

I don't know which librararies, that do the job. [COLOR="Red"]Let us hope someone else reading this thread knows and can tell if some particular package(s) should be purged and reinstalled.[/COLOR]

---

### Post by johan_olsen on 2012-04-01
I have tested and found this: I can open other pdfs not made by me, also those with several pages. And the grey nois varies from page to page, it is not the same pattern on every page.

---

### Post by WasMeHere on 2012-04-01
> **johan_olsen said:**
> I have tested and found this: I can open other pdfs not made by me, also those with several pages. And the grey nois varies from page to page, it is not the same pattern on every page.
The image data are good, and good jpg files can be created. It is the software creating the pdf file from the image data, that is buggy. I think this information helps finding a solution (although I don't know how to do it).

---

### Post by johan_olsen on 2012-04-01
I thought so too, strange thing is that it used to work perfectly. Has there been an upgrade on this software lately?

---

### Post by WasMeHere on 2012-04-01
> **johan_olsen said:**
> I thought so too, strange thing is that it used to work perfectly. Has there been an upgrade on this software lately? Probably. If you have the endurance, try to file a bug report...

---


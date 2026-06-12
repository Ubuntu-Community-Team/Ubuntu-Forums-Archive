---
title: "Automatic (Re) Pagination"
date: 2006-10-11
forum: Art &amp; Design
---

### Post by notarikon on 2006-10-11
Hi, I'm looking at printing out a PDF file of a few hundred pages, but want to lay it up as two-up per A4 to both reduce the amount of paper I use and also make it easier to hold (going to bind it into a proper book at the end).

The problem is, I wish to make the pages double sided, however, this will mean that the page numbers will no longer match up on the front & back - is there any software available that will automatically relay the pages for me in the correct order for printing?

I've tried Scribus, but it refuses to load any of my PDFs :)

---

### Post by eeGhoong0ais on 2006-10-12
```
sudo apt-get install mpage
```Depending on whether your printer can manage double-sided output, you'll want either the -e option or a couple of runs with -O and -E. There are lots of options, and the man page is pretty good.

---


---
title: "Invert colors in pdf"
date: 2009-07-25
forum: Assistive Technology &amp; Accessibility
---

### Post by Phyrexicaid on 2009-07-25
I am using Ubuntu netbook remix.

I read quite a few ebooks on my netbook, screen is the perfect size once I've rotated the page.  Only problem is, black on white isn't great for the eyes.

I know I can invert the PDF using mogrify directly, but the end quality is terrible (not good for reading).  I can also use imagemagick to convert the PDF to images, invert, then back to PDF.  That works, but is very time consuming.

How can I invert quickly?  Foxit reader for windows has this capability, but not the Linux version.

---

### Post by Phyrexicaid on 2009-07-26
> **Phyrexicaid said:**
> I am using Ubuntu netbook remix.

I read quite a few ebooks on my netbook, screen is the perfect size once I've rotated the page.  Only problem is, black on white isn't great for the eyes.

I know I can invert the PDF using mogrify directly, but the end quality is terrible (not good for reading).  I can also use imagemagick to convert the PDF to images, invert, then back to PDF.  That works, but is very time consuming.

How can I invert quickly?  Foxit reader for windows has this capability, but not the Linux version.

I am now running the windows version of Foxit under Wine, seems to work.  Download the zip file, not the executable installer.

(A native solution would have been nice though)

---

### Post by notlistening on 2009-07-26
If you are using compiz then you can choose to put any window or the whole screen into negative by using the  keyboard Windows button + m for everything and + n for an individual window. Then use the same combination of the windows buttons the scroll wheel on a mouse to zoon in and out still with good quality.

---

### Post by arky on 2009-08-06
Run xpdf -rv (reverse video) option

$xpdf -rv <filename>

---


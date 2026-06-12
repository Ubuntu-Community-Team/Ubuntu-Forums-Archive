---
title: "[SOLVED] Replacement for .wmf files?"
date: 2007-08-28
forum: Absolute Beginner Talk
---

### Post by NovaAesa on 2007-08-28
What would be a good replacement for .wmf files in Ubuntu? Specifically I want to use them to store mathematical formula. In Windows I used a program called Maths Type. I would put the .wmf files into a power point presentation and use it for studying purposes. When I opened these files using open office, they formating was all weird, and I understand that Ubuntu cannot use .wmf files. Is this correct?

Does anyone have a good format for replacement? Do you know of any programs for Ubuntu that can make maths formulas into image files?

---

### Post by vanadium on 2007-08-28
wmf's are probably enhanced metafiles and indeed, open source has some trouble reading these properly. There are less problems with the older "plain" metafiles. More common "Generic" vector graphic formats are svg (scalable vector graphics, editable with inkscape), eps (encapsulated postscript, not editable) and pdf (not editable).

There are solutions in open source land to create math formula's. The unsurpassed tool is and remains Latex. It is the only way to create real perfect math formulas that meet the highest quality standard.

For more modest needs, you will find that openoffice.org math is very satisfactory. These are created as OLE objects into regular openoffice documents (text, presentations) and thus can be easily adapted afterwards.

I do not see a way with these specific tools to quickly save these into a generic graphics format (eps, pdf, png) as individual files though.

---

### Post by NovaAesa on 2007-08-28
Thank you. It seems Latex is the way to go. I found an editor called Kile, so I shall give that a try.

---


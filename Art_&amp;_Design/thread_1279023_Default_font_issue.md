---
title: "Default font issue"
date: 2009-09-30
forum: Art &amp; Design
---

### Post by Vaphell on 2009-09-30
issue:
default font is outstanding, my favorite in general but some letters i happen to see quite often (polish chars) look bad when using different rendering engines

when using 'best shape' - **&#380;** has dot horribly off, far to the left (it should be centered)
when using 'subpixel smoothing' - base shape of the letter **&#281;** should be just like e and it is not
examples in attachments.

question: where to go to have this annoying visual issue fixed?

---

### Post by Newfoundlander on 2009-09-30
Do these letters render better if you increase or decrease the font by one point size?

For my size screen, most fonts are 10 points in size but other look best at 11 points.

---

### Post by Vaphell on 2009-09-30
e&#281; - horizontal line is usually 1px down for &#281;, for some sizes these lines are properly placed (ie 12), effect disappears at size ~25

&#380; - odd sizes are ok, even are off - effect dissapears at size ~18

i guess there are some slight imperfections in the vector representations of these letters and due to rounding in calculations there is that +/-1px difference.

What is the default sans font? Dejavu? Bitstream?

edit: it appears that all e derivatives with modifiers below look different than the rest

---

### Post by mcduck on 2009-10-01
> **Vaphell said:**
> issue:
default font is outstanding, my favorite in general but some letters i happen to see quite often (polish chars) look bad when using different rendering engines

when using 'best shape' - **&#380;** has dot horribly off, far to the left (it should be centered)
when using 'subpixel smoothing' - base shape of the letter **&#281;** should be just like e and it is not
examples in attachments.

question: where to go to have this annoying visual issue fixed?

Have you set the DPI to correct value for your monitor? Using wrong DPI will pretty much always result in that kind of problems..

---

### Post by Vaphell on 2009-10-01
nah, i see these glitches on various displays on various computers

i assumed that the font in question is dejavu sans, so went to the dejavu irc channel and one of the devs confirmed he sees that incosistency in the look of e derivatives and that there are some issues with dots.

update: it appears that hinting set to light + subpixel smoothing for lcd causes that o_O

---


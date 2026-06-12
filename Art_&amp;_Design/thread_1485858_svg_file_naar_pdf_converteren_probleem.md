---
title: "svg file naar pdf converteren probleem"
date: 2010-05-17
forum: Art &amp; Design
---

### Post by janneman37 on 2010-05-17
Hallo,

Hoe kan ik een svg file naar pdf converteren. De svg file bevat schuingedrukte tekst. Elke keer als ik converteer met inkscape wordt deze schuingedrukte tekst terug rechtgezet. Ik heb ook al imagemagick geprobeerd, maar qualiteit is daar niet goed. Het rare is wanneer ik de svg file open in inkscape op windows de tekst ook recht staat, terwijl in ubuntu de tekst wel schuingedrukt staat. Het zou naar pdf moeten geconverteerd worden om in latex te kunnen importeren.

Alvast bedankt.

---

### Post by Newfoundlander on 2010-05-17
I hope you can read my English.  I translated your message because I do not read Dutch myself.

The easiest thing to do is convert the text to a path.  Select the text, choose Path in the top menu, Object to Path.  If you want to edit the text again later, save a different version before you convert the text .

It sounds like your problem is caused by "fake italics".  When a font does not have an actual italic version, the software will put the lettering on a slant to make it look italics -- this is "fake italics".  Try changing the font to one that has an italic version.

Hope this helps.

---


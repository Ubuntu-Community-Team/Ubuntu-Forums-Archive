---
title: "kerning fontforge"
date: 2008-02-12
forum: Art &amp; Design
---

### Post by Smbrandes on 2008-02-12
Does  anyone know how to get fontforge to apply the kerning tables to a saved font? I have tried over and over to save a font I am working on and for whatever reason the kerning data does not stick to the font. It would be a useful trick to figure out as the font requires kerning. I have tried different standards, such as saving to true type and open font and what have you but nothing seems to work. Is there some sort of system wide kerning table that must be accessed? All the other fonts I have examined that have kerning have the name "kern" horizontal kerning in Latin lookup. Sounds like a conspiracy. However I have not any idea if that is a separate entity for all fonts or if you can just make your own table or what. Anyway,  the kerning thing is the last hurdle to a usable font.

---

### Post by Smbrandes on 2008-02-13
solution for generating kerned opentype fonts. 

metrics-autokerning

look to box new lookup table click on it which brings up a dialog box called "lookup." In this box at the top there is a small box that says 'feature' click the tiny little gray rectangle under it to reveal several options, use horizontal kerning. Then enter the name of the kerning table in the bottom entry box that asks for a new name. This results in a smaller dialog box appearing which asks for the subtable name, just add 'subtable' to the name of the lookup table previously named. Then click o.k. Now a box appears asking for kerning format. I used 'by pairs' then hit enter go back to the auto generate dialog box that you first opened from the menu metrics-autokerning. Set the distance to something you guess would be useful. Then at File-Generate font use OpenType (cff). Hope that was useful enough explanation.

This also works to generate True type fonts. 

Problem mostly solved

---

### Post by Smbrandes on 2008-02-16
After working a it with the generated fonts there remains several major issues. First it only functions reasonably well under the gnome text editor. Here it leaves too much space between words and does not deal well with any of the punctuation. Under Open Office it fails miserably as the kerning disappears. The same for under any windows applications. So, how to resolve mapping the proper kerning in a font that the above applications will use satisfactorily remains unanswered.

---

### Post by Smbrandes on 2008-02-26
Apparently microsoft does not support actual kerning they use some other bizarre method. theoretically Adobe products do, I have yet to boot to windows to test this.

---

### Post by typovar on 2008-06-23
Open a New Metrics windows from the menu Window;
Then File | Merge Feature Info and select the metrics file you would like to use. 
[http://fontforge.sourceforge.net/metricsview.html]("http://fontforge.sourceforge.net/metricsview.html")
documentation on Lookups :
[http://fontforge.sourceforge.net/fontinfo.html#Lookups]("http://fontforge.sourceforge.net/fontinfo.html#Lookups")

---

### Post by Smbrandes on 2009-05-19
Finally worked out the whole kerning business. It is just tedium.

---


---
title: "Problem with ttf fonts"
date: 2008-10-31
forum: Art &amp; Design
---

### Post by threegremlins on 2008-10-31
I do design work and I have a large number of fonts, is there a maximum number of fonts Ubuntu can handle? I've never had this problem before, gimp doesn't show the sample  icons for the different fonts and produces an arial type font for most of the ones I added, inkscape shows the font name but the sample is just a string of boxes, xaralx only displays a limited number of fonts but they display properly on the page.  I added them to /usr/share/fonts in their own folders and to ~/.fonts in my home folder and ran the fc-cache -vf command, with and without sudo. Any ideas?

Also, launching the programs in terminal window, I get the message "WARNING Pango something or other,,,,and,,,,,cairo scalable fonts,,, expect ugly something or other." 
Well ain't that perfectly clear;)

---

### Post by AJB2K3 on 2008-11-01
Pass but Fontmatrix allows you to switch off fonts reducing the amount of font programs have to load.
Would help if you could actually post the full error message.

---

### Post by threegremlins on 2008-11-01
This is what shows up opening inkscape, when you hit the text icon you get more when as inkscape tries to access the fonts.

(inkscape:7103): Pango-WARNING **: failed to create cairo scaled font, expect ugly output. the offending font is 'Eras Lt BT 9.9990234375'

(inkscape:7103): Pango-WARNING **: shaping failure, expect ugly output. shape-engine='BasicEngineFc', font='Eras Lt BT 9.9990234375', text='AaBbCcIiPpQq12369$€¢?.;/()'

---

### Post by AJB2K3 on 2008-11-02
Just out of curiosity try deleting the font Eras Lt BT (temperary)

---


---
title: "[SOLVED] Openoffice: How do I switch language on spellcheck?"
date: 2007-08-22
forum: Absolute Beginner Talk
---

### Post by jingo811 on 2007-08-22
> **Choose Tools > Options > Language Settings > Writing Aids**
.....in the Available language modules list, select one of the language modules and then click Edit.

I looked for the built-in help in Open office regarding switching language on the spell check.  I can't make it work or maybe my English is to bad to follow its instructions.
Anyhow I'm able to choose Swedish on Edit, I OK it restart Open office.  But the check mark still use english as default.  How do I make things work?

I managed to switch the Default document language to Swedish though but that doesn't spell check at all.

---

### Post by daradib on 2007-08-23
First try: Select text -> Format -> Character -> Select language. If this doesn't work, continue reading.

Hit F11. This brings up the Styles and Formatting pane. Right click Default and select Modify. Go to the Font tab and change the language.

If you want to change this setting permanently and not just in one particular document, you need to set up a template based on a blank documents settings. So create a new document. Change the font/language settings as you so desire. Then select File>Templates>Save. Type in the template name (whatever you like). Then File>Templates>Organise. Expand the My Templates pane and right click the Template you created and select Set as Default Template.

Tell me if this helps.

---

### Post by jingo811 on 2007-08-23
I tried these 2 suggestions not the third one since the previous ones didn't work.
None of them were able to change the situation since I already had set those settings to Swedish previously.

> First try: Select text -> Format -> Character -> Select language. If this doesn't work, continue reading.

Hit F11. This brings up the Styles and Formatting pane. Right click Default and select Modify. Go to the Font tab and change the language.

Could it be that I haven't installed a Dictionary file for my Swedish spell check?

---

### Post by Aishiko on 2007-08-23
don't know you could see if there are any packages or addons for open office in the data base or perhaps download a swedish version from the OpenOffice website.

---

### Post by jingo811 on 2007-08-23
> don't know you could see if there are any packages or addons for open office in the data base or perhaps download a swedish version from the OpenOffice website.

I need both an English and Swedish spell checker.  Installing a new OpenOffice for each language I intend on working with seems a little extreme :)  
Isn't there a lighter solution?

---

### Post by Hagar Delest on 2007-08-23
Have a look at this thread, check if the Swedish dictionary is installed and see if paragraph style is correctly configured : [[Tutorial] Spell check and Language configuration](http://www.8daysaweek.co.uk/forums/viewtopic.php?t=758).

---

### Post by mcarni on 2008-07-06
Hi jingo811


I installed the following package throuigh synaptic and now I have Swedish spellcheck

myspell-sv-se
"Swedish (SE) dictionary for myspell"


Hope this helps


M

---

### Post by jingo811 on 2008-07-06
Tnx for the tip!  Also anybody know how to combine a Swedish and English dictionary together?  I have to teach oOffice every single word it feels like when I spellcheck.

---

### Post by mcarni on 2008-07-06
I found a "quick and dirty" solution, I'm sure there are better ways, hopefully someone will give you a cleaner solution but if you are in a desperate situation you can copy the whole content of the English dictionary and paste it in the Swedish dictionary. I added a couple of non Swedish words to my Swedish dictionary (sudo gedit /usr/share/myspell/dicts/sv.dic) and everything went fine. 

Let us know
M

---

### Post by jingo811 on 2008-07-06
I like "Quick and Dirty" solutions :) tnx!

---

### Post by mcarni on 2008-07-06
glad to help


M

---


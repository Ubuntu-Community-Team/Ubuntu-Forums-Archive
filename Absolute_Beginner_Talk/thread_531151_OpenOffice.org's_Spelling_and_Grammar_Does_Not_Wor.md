---
title: "OpenOffice.org's Spelling and Grammar Does Not Work Well (for me)"
date: 2007-08-21
forum: Absolute Beginner Talk
---

### Post by wersdaluv on 2007-08-21
I wrote my term paper on OpenOffice.org Writer. I did not have big issues with it until I noticed a while ago that its grammar and spelling check is horrible. When I opened my term paper using MS Word, it noticed a lot of spelling and grammar errors while in OpenOffice.org Writer, I was not notified.

Are there additional options that are not activated in, or addons that are not included in OpenOffice.org Writer for it not to efficiently check my grammar and spelling?

---

### Post by vanadium on 2007-08-21
There is no grammar checker for Openoffice.org. The English spell checker should be quite OK though. If a lot of your errors were uncaught, then perhaps the language was perhaps set to a language for which no spelling checker is installed on your system.

* In Tools - options - language settings  - Writing Aids, you can press an "edit" button. In the Edit modules dialog that appears, there is a drop down. Only for the languages that have a blue checkmark (with "ABC") dictionaries are installed. Additionally, they will only be in effect when the checkmarks in the dialog are marked.

* The language in OOo is a character formatting feature. In Tools - Options - language settings - Languages, you can set the default language that should be in effect for new documents created using File - New. To change the default language for an already created document, you need to change the Default style. Press F11 (toggles on and off) to display Styles and Formatting. Look for the default style, right-click, modify, and on the character tab, set the language of your choice. Also in this drop-down, you can see wether the dictionaries of a language you choose are installed or not. Be careful: the langage setting can be overwritten by a style that depends on the default style. If that is the case, you need to remove the language setting from the style that depends on the default style (styles are hierarchical in OOo: a style can inherit all settings of its "mother" style and just change a few aspects on its own).

* To install new langage modules, you can use the Install new dictionaries wizard (under the File menu).

Ooo is not a "clone" of MS Word. It is deceptively powerfully, but power sometimes comes at the price of some complexity.

---

### Post by wersdaluv on 2007-08-21
> **vanadium said:**
> There is no grammar checker for Openoffice.org. The English spell checker should be quite OK though. If a lot of your errors were uncaught, then perhaps the language was perhaps set to a language for which no spelling checker is installed on your system.

* In Tools - options - language settings  - Writing Aids, you can press an "edit" button. In the Edit modules dialog that appears, there is a drop down. Only for the languages that have a blue checkmark (with "ABC") dictionaries are installed. Additionally, they will only be in effect when the checkmarks in the dialog are marked.

* The language in OOo is a character formatting feature. In Tools - Options - language settings - Languages, you can set the default language that should be in effect for new documents created using File - New. To change the default language for an already created document, you need to change the Default style. Press F11 (toggles on and off) to display Styles and Formatting. Look for the default style, right-click, modify, and on the character tab, set the language of your choice. Also in this drop-down, you can see wether the dictionaries of a language you choose are installed or not. Be careful: the langage setting can be overwritten by a style that depends on the default style. If that is the case, you need to remove the language setting from the style that depends on the default style (styles are hierarchical in OOo: a style can inherit all settings of its "mother" style and just change a few aspects on its own).

* To install new langage modules, you can use the Install new dictionaries wizard (under the File menu).

Ooo is not a "clone" of MS Word. It is deceptively powerfully, but power sometimes comes at the price of some complexity.

Wow. That's an amazing answer.

:KS

By the way, how do I change the language module? Whenever I change "English (Philippines)" (it has no blue check with "ABC) to "English (USA)," the changes are not applied. What I do is to Choose English (USA) from the drop down menu then click close then click "OK" under "Options."

How do I apply changes to the language module? :KS

---

### Post by wersdaluv on 2007-08-21
I'm really puzzled. The spellcheck notifies me because of the spelling of the word "Lasallians" but it does not even notice the spelling error whenever I type "thier."

---

### Post by Hagar Delest on 2007-08-22
For language configuration, see here : [[Tutorial] Spell check and Language configuration](http://www.8daysaweek.co.uk/forums/viewtopic.php?t=758).

---


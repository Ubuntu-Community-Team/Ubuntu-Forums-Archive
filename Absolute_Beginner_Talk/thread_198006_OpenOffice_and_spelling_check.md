---
title: "OpenOffice and spelling check"
date: 2006-06-16
forum: Absolute Beginner Talk
---

### Post by viniciuscarvalho on 2006-06-16
Hello there! I have ubuntu configured using US-English as default language, but I need my documents to have Portugues-brazil spelling check. The only way ?I could do this was changing the entire locale (I hate app menus in portuguese, most of the time translation sux). Is there a way to keep all my menus and apps with English menus and have a brazilian spell checker?

Regards

---

### Post by bruce89 on 2006-06-16
Just install myspell-pt-br with this command ```
sudo apt-get install myspell-pt-br
```

---

### Post by brentoboy on 2006-06-16
I wish I could help you here... but on a different note, you should consider contributing to the Portugues-brazil translation packages, if their translations are terrible, then they are probably looking for a guy who would be willing to contribute some more understandable translations.

that said, maybe there is a way to run a single app in a different local, like the gksu app can run things as a different user.

sorry I cant be of more help.

---

### Post by viniciuscarvalho on 2006-06-16
[QUOTE=bruce89]Just install myspell-pt-br with this command ```
sudo apt-get install myspell-pt-br
```[/QUOTE]

Well that did not work either. I choose the default language on Tools -> Options -> Language Settings :

Locale Settings -> Portuguese (Brasil)
Default Language for docs
Western -> Portuguese (Brasil)

But what happens is that instead of changing the dic, it seems that no dic is present at all. It allows me to type and never it underlines the misspelled ones...

any ideas?

---

### Post by bruce89 on 2006-06-16
[QUOTE=viniciuscarvalho]Well that did not work either. I choose the default language on Tools -> Options -> Language Settings :

Locale Settings -> Portuguese (Brasil)
Default Language for docs
Western -> Portuguese (Brasil)

But what happens is that instead of changing the dic, it seems that no dic is present at all. It allows me to type and never it underlines the misspelled ones...

any ideas?[/QUOTE]
The command above installs the pt-br dictionary.

---

### Post by steve.horsley on 2006-06-16
Under Tools->Options, then Language Settings->Languages you can independently set the interface language and the default document language.

Additionally, if you right-click a paragraph and choose Edit Paragraph Style, under the Font tab you can change the language setting specifically for that paragraph style.

---

### Post by Odisej on 2006-07-04
I have a related question. I would like to use Slovenian language for spellchecking but the OOo never remebers it as a default selection. Meaning that always when I open a new document the spelling is set to English and I have to manually change it to Slovene (and it gets annoying). 

Apperently this is linked to the "Language Support" in Ubuntu but I do not wish to use an interface in my native language as I am used to the English one and always get lost if I use any other language.

Is there a way I can make Slovenian a default spellchecking language but still keep English interface.

Will be grateful,

Odisej

---

### Post by someusernoob on 2006-07-04
Try this, worked for me:

OpenOffice.org 2 Writer - Using new default template
Templates can save frequently used settings such as spacing, fonts, and language. By setting a new template as a default, you can open new documents with your custom settings.

Create a document with the styles set with the spacing, fonts and language* you want to use.
**File > Templates > Save...**
Click **My Templates** to view currently available templates
Name Your template
Click **Save**
**File > Templates > Organize...**
In the tree on the left, click the folder icon beside My Templates to expand the tree.
Right click your new template.
Select **Set as default template**
Click **Close**

*Tools > Options > Language Settings > Languages > Default languages for documents

---

### Post by Odisej on 2006-07-04
It works! Thank you for your help. Would buy you a beer if you were closer. :)

---

### Post by someusernoob on 2006-07-04
Great! Ill get myself a beer then :P Its 35 degrees here, i really can use one :D

---

### Post by zeca_pedra on 2006-08-18
Let me also thank you! I was having a terrible problem setting portuguese (Portugal) as my default language for documents globally - that is, without having to change the setting everytime I opened OpenOffice... with your suggestion I solved that :D 

But still, this is a major bug in version 2 of this great office suite: how it is possible that the check mark near «For this document only» it's greyed and, as a consequence, not acessible for the common user to change?

This issue surely must be reviewd the next version [-o< 

Thank you very much \\:D/ 
Zeca

---


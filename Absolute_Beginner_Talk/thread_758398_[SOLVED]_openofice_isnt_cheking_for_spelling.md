---
title: "[SOLVED] openofice isnt cheking for spelling"
date: 2008-04-18
forum: Absolute Beginner Talk
---

### Post by patchido on 2008-04-18
well i dont know why.. i am writting in spanish and ii wont get the red underline neighter errors when i click spellcheck any help

---

### Post by bumanie on 2008-04-18
In open office writer go to  Tools - Options - Language Settings - Writing Aids, and ensure that the Check in all languages check box in the Options list is selected.

---

### Post by talsemgeest on 2008-04-18
Go tools>options>language options or something like that and check the language. If it has an "abc" tag next to it, it has spellchecking. If it doesn't spellchecking doesn't work.

---

### Post by patchido on 2008-04-18
still cant make it work :(

---

### Post by patchido on 2008-04-18
wait a second does Oo have dictionaries for other languages than english?

---

### Post by Zill on 2008-04-18
Spell checking applies to the particular document.

Select the entire document (Ctrl-a) then menu Format, Character.  Select your desired language from the pull-down list.

---

### Post by talsemgeest on 2008-04-18
Does the language you have selected have a little ABC next to it? If it doesn't, switch to one that does or download one.

---

### Post by sam_delta on 2008-04-18
if you cant select spanish , or you select it and it dosnt work you need to install the language package

you can either 
click file > wizards > dictionary install (in open office)
or you can 
go to synaptic and install a package called aspell-es for spanish

tell us how it goes
sam

---

### Post by patchido on 2008-04-18
i did the aspell thing cause the other didnt work.. so now what it should work alone?

---

### Post by talsemgeest on 2008-04-18
Openoffice checks from the language you tell it too. As long as you have selected the right language, and that language has a dictionary attached (i.e. "ABC") you spellchecking will work.

---

### Post by Can+~ on 2008-04-18
```
sudo apt-get install language-support-es
```

Esto instalará todas las librerías necesarias, si estás usando ubuntu en inglés (como yo) pero quiere soporte en es español.
/en/This will install all the necessary libraries for translation, in case you're using english ubuntu (like me) but want spanish writing.

```
metapackage for Spanish; Castilian language support 
This metapackage depends on all packages that provide native language
support for applications in Ubuntu (like spell
checkers, dictionaries, OpenOffice and Mozilla locale packages,
etc.).

If you also want your applications and the desktop to be translated,
please additionally install language-pack-es.

Language: Spanish; Castilian
```

---

### Post by patchido on 2008-04-19
> **Can+~ said:**
> ```
sudo apt-get install language-support-es
```

Esto instalará todas las librerías necesarias, si estás usando ubuntu en inglés (como yo) pero quiere soporte en es español.
/en/This will install all the necessary libraries for translation, in case you're using english ubuntu (like me) but want spanish writing.

```
metapackage for Spanish; Castilian language support 
This metapackage depends on all packages that provide native language
support for applications in Ubuntu (like spell
checkers, dictionaries, OpenOffice and Mozilla locale packages,
etc.).

If you also want your applications and the desktop to be translated,
please additionally install language-pack-es.

Language: Spanish; Castilian
```

worked perfectly.. thanks a lot

---


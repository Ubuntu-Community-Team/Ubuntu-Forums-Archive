---
title: "Is Open Office compatible with MS Office."
date: 2007-05-02
forum: Absolute Beginner Talk
---

### Post by a.v.l on 2007-05-02
Why is it that an open office spreadsheet document (.ods file) created in Ubuntu, cannot be opened in Windows XP.  I was under the impression that MS office and Open office were compatible with each other .

This is my first attempt at doing some serious work since completely migrating from MS. I needed to create a spreadsheet and upload it to a  group for other MS windows users to access, unfortunatly it didn't open for them.  I can access the spreadsheet myself by using Linux  but other window users cannot open it. Is this likely to be an isolated case or are there other similar conflicts I will come accross.  I'm hoping this is can be made to work.

---

### Post by Seisen on 2007-05-02
You should have an option of saving the file in .xls

---

### Post by thecomputingexpert on 2007-05-02
open office has their own formats but you can save a document in the ms office format as well

---

### Post by jkblacker on 2007-05-02
I'm fairly sure OpenOffice has an option to save as MS formats - this would be where the compatibilty comes in. Or, save text documents as .rtf files which are compatible. For spreadsheets you'll have to use .xls, but as I said I think OpenOffice can save in that format.

---

### Post by silkstone on 2007-05-02
OpenOffice can read and save as MS Office format (.doc, .xls, etc) but MS Office cannot read .odt and .ods files. To open the spreadsheet in Excel, Save As .xls from Calc.

You can get a plugin from Sun that allows MS Word to read .odt files, but I'm not aware of one that lets Excel read .ods.

---

### Post by Cypher on 2007-05-02
Well, first of all, OpenOffice is compatible with MS Office documents, but not the other way around. MS Office will nicely ignore anything that OpenOffice will create. If you wish to create documents to be openedin MS Office, you have to create them in MS Office's format..not in the native format of Open Office..

So, try creating an Excel-compatible file with Open Office Spreadsheet and see if your group has better luck with that..

---

### Post by aysiu on 2007-05-02
MS Office doesn't support open standards.

OpenOffice and MS Office are compatible because OpenOffice has managed to figure out how to use Microsoft's proprietary .doc format. If Microsoft wanted to be more cooperative, they'd open up .doc or make MS Office compatible with .odt.

---

### Post by jkblacker on 2007-05-02
Tho, of course, Office 2007 now has yet another set of different standards - .docx and so on, iirc from the beta! I'm not sure if or when OpenOffice will work those ones out...

---

### Post by thefoolisme on 2007-05-02
Since we're on the subject, let me ask this.  

I create a document in Word, and save it.  I then open the doucment up in OO, and it's fine.  I create a document in OO, save it in .doc format, and then open it in Word, and all the fonts are messed up.  Can that be fixed?

True type fonts I thought were universal.  Is there a way to get those two programs to both have Times New Roman, and Courier new fonts for universal compatibility?

---

### Post by a.v.l on 2007-05-02
Thanks everyone, just going to try saving in a MS format.

---

### Post by lamalex on 2007-05-02
> **thefoolisme said:**
> Since we're on the subject, let me ask this.  

I create a document in Word, and save it.  I then open the doucment up in OO, and it's fine.  I create a document in OO, save it in .doc format, and then open it in Word, and all the fonts are messed up.  Can that be fixed?

True type fonts I thought were universal.  Is there a way to get those two programs to both have Times New Roman, and Courier new fonts for universal compatibility?

apt-get install msttcorefonts

---

### Post by silkstone on 2007-05-02
> **thefoolisme said:**
> True type fonts I thought were universal.  Is there a way to get those two programs to both have Times New Roman, and Courier new fonts for universal compatibility?

Install the msttcore fonts package from Synaptic, then configure OO to use those by default - e.g. Times New Roman in Writer. You can also add extra TrueType fonts just by dragging and dropping them into the fonts folder.

EDIT/ Beaten to it. :)

---

### Post by Seisen on 2007-05-02
That is part of the problem of using OpenOffice, its not a perfect replacement for Word but its pretty close. Take notice that they give you a warning when saving the file about formats and other things.

---

### Post by a.v.l on 2007-05-02
Thanks, it worked.

One other question:

When I save the spreadsheet to my home folder the title appears as I've typed it, but when its opened as a MS or even an Open office document the title appears with symbols and capitals in between. 

Example:
This is how I wrote it.

"Spreadsheet of last six months"

and this is how it appears when opened . (Or something similar)

"Spreadsheet of lastAO%FY%HG% six months"

Why is that?

---

### Post by Xarok on 2007-05-02
> **a.v.l said:**
> Thanks, it worked.

One other question:

When I save the spreadsheet to my home folder the title appears as I've typed it, but when its opened as a MS or even an Open office document the title appears with symbols and capitals in between. 

Example:
This is how I wrote it.

"Spreadsheet of last six months"

and this is how it appears when opened . (Or something similar)

"Spreadsheet of lastAO%FY%HG% six months"

Why is that?

Do you have multiple language inputs on your system and perhaps used a different one?
Does this happen often?
If you try re-typing it does it still mess up?

---

### Post by a.v.l on 2007-05-02
> **Xarok said:**
> Do you have multiple language inputs on your system and perhaps used a different one?
Does this happen often?
If you try re-typing it does it still mess up?

How do I check if I have multiple languages inputs on my system please. I've typed it several times and still it remains the same.

---

### Post by lakersforce on 2007-05-02
Word is perfectly compatible with the OpenDocument format. You just have to download a [plugin]("http://www.sun.com/software/star/openoffice/index.xml") to make it work.

---


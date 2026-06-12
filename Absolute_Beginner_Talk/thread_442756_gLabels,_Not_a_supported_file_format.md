---
title: "gLabels, Not a supported file format"
date: 2007-05-13
forum: Absolute Beginner Talk
---

### Post by Sabar on 2007-05-13
I am currently trying to import a file from another computer that is running Microsoft office.

Background Information

I am using a Attache 512m to take a file made and saved from Microsoft Word for labels and import it into gLabels.

Unfortunately when I try this what I get is this error

Could not open file "/media/USB DISK/Copy of Ms. labels.doc"
Not a supported file format

Is there any way to get gLabels to recognize this file format? and read it?

If more information is needed please let me know. Oh yea I am also running feisty fawn. 
if there is a better place to post this question please let me know.

Sabar

---

### Post by wmichaelb on 2007-05-15
Sabar: I'm running Dapper, but I suspect that the exact flavor of OS has nothing to do with it.  I went through this drill a few days ago, and I believe that glabels doesn't work like we might think it does. 

Rather than simply opening a file, you need to perform a document merge, which should work with a comma-delimited file (file ends in .csv). Microsoft apps should have a file/export function which will create such a file, and that can then be imported into glabels via the document merge function. Open glabels, click on the "help" tab, and look up "document merge" for details. Basically, one must first create a new document that fits whatever particular label you're using, and then a new dialog box will open with a gridded window to use for layout. Click on Objects, and then Merge, and you'll find a way to choose the csv format and import the file.

Good luck!

---


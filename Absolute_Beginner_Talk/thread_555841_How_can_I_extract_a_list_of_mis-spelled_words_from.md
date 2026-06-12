---
title: "How can I extract a list of mis-spelled words from a text document?"
date: 2007-09-20
forum: Absolute Beginner Talk
---

### Post by teasum on 2007-09-20
I would like to extract a list of all unrecognized or mis-spelled words from an OpenOffice (.odt) or Word (.doc) file.  Does anyone know if there is a way to do this?  

Some background:  I have an extensive set of lecture notes, and I would like to quickly extract a list of terms with odd-spellings for students.  I could go through and do this by hand, but I have to think there is a way to pull out a list of all unrecognized words in a text/odt/doc file.  Any ideas?

---

### Post by ncappel1 on 2007-09-21
it is possible to extract a list of words from regular text files with aspell. the command would be:
```
cat [file.txt] | aspell list > [newfile.txt]
```
don't know if it will work with office documents, however.

hope this is helpful

---

### Post by teasum on 2007-09-23
Thanks--this worked.  I just copied the contents of the office file (odt or doc) into a text file, and ran the command you gave.  This will be a real time-saver.

---

### Post by mlissner on 2008-03-01
There's a better way: 
odt2text [file.txt] | aspell list > [newfile.txt]

---


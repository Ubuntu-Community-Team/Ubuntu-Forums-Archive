---
title: "[SOLVED] Open Office"
date: 2008-03-10
forum: Absolute Beginner Talk
---

### Post by ellalan on 2008-03-10
I am unable to read down loaded documents with Open office writer, could someone help me.

---

### Post by FuturePilot on 2008-03-10
Please provide some more details. What happens when you try to open a document? Crash? Freeze? Are there any errors if you try to reproduce the problem when running it from a terminal?
Run
```
oowriter
```
Try to open a document. Post any errors here.

---

### Post by forrestcupp on 2008-03-10
And what kind of documents are you trying to read?  What is the filetype, ie .doc, pdf.

If you are trying to open a .docx file, which is MS Office 2007's new format, it won't work in OpenOffice, yet.  If that is the case, go to [Zamzar](http://www.zamzar.com/) and use their web-based conversion utility to convert it to a format that OO will open, like doc.

---

### Post by ellalan on 2008-03-10
It is .tar file type and it was a document provided by Canon, I have to get in touch with Canon to provide the information by some other means. Thank you for the response.

---

### Post by RequinB4 on 2008-03-10
A .tar is a compressed archive, much like a .zip or a .rar.  Simply right click and "extract here" to view the encoded files.

---

### Post by Charcoal1981 on 2008-03-10
.tar is an archive file - like .zip (but possibly without compression). You need to extract it first. either right click and use archive manager to extract or use
```
tar -xvvf filename.tar
```
then try opening the extracted files with openoffice

---

### Post by ellalan on 2008-03-10
Thank you all guys
forrestcupp, Zamzar is a useful link for me.

Happiness eez Ubuntu.

---


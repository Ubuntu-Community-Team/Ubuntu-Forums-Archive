---
title: "How to do a find and replace through terminal?"
date: 2006-10-30
forum: Absolute Beginner Talk
---

### Post by Bagboy23 on 2006-10-30
Does anyone know how to do a find a replace on files. For instance I have a file called Resume.doc and in it, I want to locate all the instances of "SAP" and replace with "MySap" but also just below "MySap" text, I want to add the version number to the next line. For example:

ASB-CRM Mods
ASB - CRM Mods2
MySap
<-------------------- want to insert version in here, but after the MySap text.
ORCL - Mods2


Any suggestions is much appreciated.

Thanks.

---

### Post by localuser on 2006-10-30
I assume that you have a text file.

If you insist that it be done at the commandline (terminal) then one way is with a utility called sed.

[http://www.grymoire.com/Unix/Sed.html](http://www.grymoire.com/Unix/Sed.html)

Is there a reason not to use a gui text editor like gedit?

---

### Post by Jussi Kukkonen on 2006-10-30
First, if it's a Word document I advice against this. Even if you can find the strings in the file, it's still a binary file and editing it could be catastrophical.

If it's a text file that just happens to have a .doc extension, the command you are looking for is *sed* (or perl or whatever floats your boat). There are many tutorials around the web, I suggest you read one.

Something that might work:
```
cat Resume.doc | sed 's/SAP/MySap/g' > Resume_.doc
```
This might work for the multiline version:
```
cat Resume.doc | sed 's/SAP/MySap\ [press ENTER]
more text/g' > Resume_.doc

```

---


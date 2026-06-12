---
title: "[SOLVED] OO question."
date: 2007-08-17
forum: Absolute Beginner Talk
---

### Post by CapitanYochua on 2007-08-17
I need to send an OO document to a window user. What should I do so they will be able to read it with microsoft office? do i need to change the .odt format? If so, how?

---

### Post by reacocard on 2007-08-17
> **CapitanYochua said:**
> I need to send an OO document to a window user. What should I do so they will be able to read it with microsoft office? do i need to change the .odt format? If so, how?

Yes you do, and its very easy. Just open the document, go to file -> save as and set the file type to microsoft word. Click save and there should be a .doc copy of the file in the same folder, that you can send to your windows-using friend.

---

### Post by mikewhatever on 2007-08-17
You can either save it as doc or turn it into pdf.

---

### Post by CapitanYochua on 2007-08-17
I saved it as a doc and opened it. The numbers got all messed up. How do I fix this?

---

### Post by HermanAB on 2007-08-17
Export it to PDF, then it won't change.

---

### Post by HermanAB on 2007-08-17
BTW, if you need maximum compatibility with Windows, then you *have* to install either the Freedom Fonts from RedHat, or the MS TrueType fonts.  It is impossible to keep the same look if the fonts are different.

---

### Post by CapitanYochua on 2007-08-17
How do i install those things?

---

### Post by p_quarles on 2007-08-17
> **CapitanYochua said:**
> How do i install those things?
```
sudo apt-get install msttcorefonts
```
As others said, though, the most surefire way to format the document correctly across platforms is to export it as a .pdf. This is only a bad option if the other person needs to be able to edit the file.

---

### Post by CapitanYochua on 2007-08-18
worked without having to change to pdf. thanks (:

---

### Post by hyper_ch on 2007-08-18
you shouldn't be sending documents as .doc or .odt but as .pdf ;) except if you want that the receiving party can do changes...

---

### Post by viajador on 2007-08-18
You can also save it in .RTF (Ritch Text Format) if you want someone to be able to edit the text. It is, in my opinion, the best cross-platform format to work with text files.

PDF is great to keep the most accurate format of the document in different OSs, but doesn't cut the cake if many people are working on the same document.

I use LyX to work alone, export it to PDF to distribute it and RTF to do team writing with non-openoffice users.

Try it someday.

---


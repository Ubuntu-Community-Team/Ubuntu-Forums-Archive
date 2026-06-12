---
title: "wps file"
date: 2007-07-23
forum: Absolute Beginner Talk
---

### Post by alienexplorers on 2007-07-23
What program do I need to read a wps file.  A friend sent me this file and he said that was the only format he could send it in.

---

### Post by Mornedhel on 2007-07-23
I think that's a Works file. (You should tell your friend to get OpenOffice.) Maybe OOo can open it, not sure about that.

---

### Post by RomeReactor on 2007-07-23
Hi. According to [Filext]("http://filext.com/file-extension/wps"), it *is* a Works document, and there's no OpenOffice support for it yet. Some people in the [OpenOffice forums]("http://www.oooforum.org/forum/viewtopic.phtml?t=247") have also come across this problem; one suggested to transform the fromat from .wps to .rtf:
```
word2x -f latex FILENAME.wps - | latex2rtf > FILENAME.rtf
```
obviously changing FILENAME for the actual name of the file. Another suggested to just rename the file from **FILENAME.wps** to **FILENAME.txt**. I don't know if these methods work, though, since I haven't had to deal with .wps files myself. Hope this helps.

---

### Post by mlentink on 2007-07-23
If this really is a Works file, the sender should be able to save it in either .doc of .rtf format. As him/her to use the "Save As"  function in Works, and then select the file format.

---

### Post by alienexplorers on 2007-07-23
Just got done asking her to resend this in a format I can read.  Thanks for the help.

---

### Post by simonjcruse on 2007-11-01
This is indeed a M$works file, if you had the same problem as me. IE no access to any of the microsoft programs i.e works or work. Then you can convert the files free at [www.zamzar.com](www.zamzar.com). Just upload the file and they email you the converted file. Hope this help as it was driving me mad for ages.

Regards Cruse.

---

### Post by Zeenomorph on 2008-01-24
I just came accross this issue and found that I could simply rename the .wps file to a .rtf file, and it came up fine.

---

### Post by lightstream on 2008-04-15
> **Zeenomorph said:**
> I just came accross this issue and found that I could simply rename the .wps file to a .rtf file, and it came up fine.

Wow - this actually works.. nice one !

---


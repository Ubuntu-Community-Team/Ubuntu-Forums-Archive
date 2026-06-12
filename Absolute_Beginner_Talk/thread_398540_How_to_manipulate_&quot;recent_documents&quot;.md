---
title: "How to manipulate &quot;recent documents&quot;"
date: 2007-04-01
forum: Absolute Beginner Talk
---

### Post by fritsmartfu on 2007-04-01
Hello!

I'm very happy with Ubuntu but one question disturbs me:
Every time I do something, even when I download some application, the document or the application is mentioned in the recent documents list, with some exeptions.
Microsoft-word *.doc files are shown, but all Open Office formats are not shown.
Some picture files are shown in recent documents, but others arn't.

How can I edit the file types how will be shown in the "recent files" list?

Thanks
Frits.

---

### Post by Skrynesaver on 2007-04-01
The recent documents list is maintained in ~/.recently-used, if you open an odt using the window manager, ie double click on the icon, then it will get added to this list, if however you open the document with OO.o it will get appended to the picklist in the file ~/.openoffice.org2/user/registry/data/org/openoffice/Office/Common.xcu If you are looking for a document recently accessed from within OO.o then open Open Office and File>Recent documents wil bring you there

---

### Post by jackmc on 2007-06-19
> **Skrynesaver said:**
> The recent documents list is maintained in ~/.recently-used, if you open an odt using the window manager, ie double click on the icon, then it will get added to this list, if however you open the document with OO.o it will get appended to the picklist in the file ~/.openoffice.org2/user/registry/data/org/openoffice/Office/Common.xcu If you are looking for a document recently accessed from within OO.o then open Open Office and File>Recent documents wil bring you there

Thanks, now I get it. Recent documents could use some work i think...

---


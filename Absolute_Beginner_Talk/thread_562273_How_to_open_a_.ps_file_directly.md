---
title: "How to open a .ps file directly?"
date: 2007-09-28
forum: Absolute Beginner Talk
---

### Post by yangli on 2007-09-28
Every time I double clicked on a .ps file, I got this. 

[IMG]http://img.villagephotos.com/p/2007-7/1268314/1.jpg[/IMG]

What should I do if I want to open this .ps file in, say, Document Viewer without showing this annoying message? Thanks.

---

### Post by Perfect Storm on 2007-09-28
Right click the file and go to **properties**

Go to **Open with** tab and choose your application you want to use to this file. If it aren't there click the **add** button.

---

### Post by yangli on 2007-09-28
Yes, I already did that, but that message still pops up. 

I found that if I right click -> **Properties** -> **Permissions** -> uncheck the box of "**allow executing file as program**", then Document viewer will open this file directly without showing that popup. But I have to manually do that for all PS files. Is there an easier way of doing that? Thanks.

> **Artificial Intelligence said:**
> Right click the file and go to **properties**

Go to **Open with** tab and choose your application you want to use to this file. If it aren't there click the **add** button.

---

### Post by psusi on 2007-09-28
Fix its permissions so it itsn't set to be executable.

---

### Post by yangli on 2007-09-28
Can I set that for all files with the same extension at once? Or I have to do that one by one?

> **psusi said:**
> Fix its permissions so it itsn't set to be executable.

---

### Post by Vixis on 2007-09-28
chmod -R -x *.ps
will change it Recursively for all .ps files in directory and subfolders.

---

### Post by yangli on 2007-09-28
thanks

> **Vixis said:**
> chmod -R -x *.ps
will change it Recursively for all .ps files in directory and subfolders.

---


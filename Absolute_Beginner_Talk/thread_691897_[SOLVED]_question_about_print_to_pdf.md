---
title: "[SOLVED] question about print to pdf"
date: 2008-02-09
forum: Absolute Beginner Talk
---

### Post by fritzgeraldyreyes on 2008-02-09
Is there a program for ubuntu that prints to pdf from almost any application? I mean an alternative to 'primopdf'...which I believe works only with windows..(it installs as a virtual printer, appears in the list of printers, and you can print to pdf directly from applications like mozilla firefox or image viewers by clicking file->print and then select your virtual printer/pdf creator)

thanks..

---

### Post by randy78 on 2008-02-09
yes
sudo apt-get install cups-pdf

---

### Post by aBitLater on 2008-02-09
ok, I set this up as a printer, and it asked me for a driver... I selected the same driver I use for my real printer, HP Color Laserjet 2800 Series (PS).  Then I printed to it, and it looked like it was doing something, but never asked me for a file name or location.

Where did the output go?

---

### Post by aBitLater on 2008-02-09
I went back to the printer setup manager, clicked "change" button for "Make and Model", selected "Generic" from the printer database, then "PDF File Generator" from the models.

Then chose, "Use the new PPD as is"

I thought that would solve it, but the same thing happens as in my last post.  This time I also tried to print a test page from the printer manager - that notified me that "Test page submitted as job 19".

---

### Post by aBitLater on 2008-02-10
ah... they are showing up in my home/me/PDF directory.  Confused at first because I never got a chance to name the file

---

### Post by hums07 on 2008-02-13
> **aBitLater said:**
> I went back to the printer setup manager, clicked "change" button for "Make and Model", selected "Generic" from the printer database, then "PDF File Generator" from the models.

Then chose, "Use the new PPD as is"

I thought that would solve it, but the same thing happens as in my last post.  This time I also tried to print a test page from the printer manager - that notified me that "Test page submitted as job 19".

When I chose my real printer as the model, the generated pdf file is blank.
It works after I chose this setting. Thanks aBitLater!

---


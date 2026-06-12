---
title: "when double clicked, php files are downloaded, not opened &amp; displayed"
date: 2007-01-19
forum: Absolute Beginner Talk
---

### Post by mikeintj on 2007-01-19
I am currently having a strange experience. Php files that I am working on (and therefore may contain syntax errors) are not being opened when I double click on them in the file manager. Instead they are being downloaded. Sometimes I get asked whether I want to display them, and even if I click on display they are still being downloaded to my desktop. I can right click and choose the option of opening in gedit, but this was never a problem before and obviously I just want to double click.

As I said, it is only happening to files that I am working on at the moment (this started today). Can anyone shed some light on this. 

Regards,

Mike

---

### Post by aysiu on 2007-01-19
These are local php files?

---

### Post by mikeintj on 2007-01-19
yes, files on my ubuntu hard drive. It now seems that all my php files are doing this i.e. files that I haven't touched for a week or so.

---

### Post by aysiu on 2007-01-19
Well, I'll tell you what's normal behavior, and you can say how your deviates from that, if at all.

If the files are local files, then you should be able to open them with a text editor (gedit, kate, mousepad), but if you want to open them with a web browser (Firefox, Konqueror, Epiphany), you'll need to install a web server and then either put your files in /var/www or symlink them to /var/www in order to preview them.

---

### Post by ardchoille42 on 2007-01-19
I believe you will need to install apache and php because those are php files and the system has no way of displaying them without a web server.

---

### Post by mikeintj on 2007-01-19
I have apache, I have been working on these files for weeks/months. This behaviour started today.

---

### Post by aysiu on 2007-01-19
> **mikeintj said:**
> I have apache, I have been working on these files for weeks/months. This behaviour started today.
File a bug report, then?

---

### Post by mikeintj on 2007-01-19
I should add that this isn't a mega problem, I can still edit my files* and view them through Apache, it is just frustrating and something that until a few hours ago had not happened before.

*I just have to right-click and choose open in text editor rather than double-clicking on the file to bring up the menu of choices and then clicking on display.

---

### Post by aysiu on 2007-01-20
Maybe it's Nautilus?

Have you seen this same behavior in Thunar or Konqueror?

---


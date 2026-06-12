---
title: "Archive File Type Not Readable"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by wmichaelb on 2007-06-15
Fellow Ubuntuns: When I reinstalled Ubuntu (Feisty) after installing a new mobo, the system created a new partition and put the old file system on it (Dapper). When I try to open my old files, I get a message that says "file type not supported". I have 7zip installed,  but can't find it to apply to the file. If I right-click on the "mike" folder, and then click on "open with", I get a long list of programs, but not 7zip, nor anything else that will open it. Does anyone have any suggestions?

Thanks in advance; you've all been great!

---

### Post by zvacet on 2007-06-16
Wich type your files are?if you have p7zip right click on file and select **unpack here**.

---

### Post by wmichaelb on 2007-06-17
zvacet: That's not the dialog box that I get. What I get is:

- Open with "Archive Manager"
- Open with ->
- Copy
- Send to...
- Extract to...
- Properties...

"Properties" says that it's a gzip archive, but if I try Archive Manager, I get a message that says "archive type not supported". My applications manager says that 7zip is installed; but I can't find it anywhere on any toolbar.
Do I need to uninstall Archive Manager, and use only 7zip? Will that even unarchive the file?

Any insight is much appreciated. Thanks!

---

### Post by zvacet on 2007-06-17
Try with **Extract to...** 

but to be absolutly sure that you have everything you need

```
sudo aptitude install p7zip-full rar unrar
```

---

### Post by wmichaelb on 2007-06-17
zvacet: This is a stubborn problem. I did as you suggested; but still get the message that the archive type is not supported. Should I try to sacrifice a red chicken, or ?

Thanks for your time!

---

### Post by FrancoNero on 2007-06-22
getting thes ame problem witha  gzip file from gnomelooks.org... weird

---


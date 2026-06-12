---
title: "[SOLVED] Automate file opening from nautilus"
date: 2008-01-10
forum: Absolute Beginner Talk
---

### Post by bitra on 2008-01-10
I have this little problem when I want to open a *.html file from nautilus file browser. When I double click a *.html file Nautilus always asking me this question:

> Do you want to run "FileName.html", or display its contents?
"FileName.html" is an executable text file.

Is there any way to customize nautilus' behavior to recognize the *.html file and automaticaly open it in a browser? Oh, I use Firefox as my default browser.

---

### Post by Paqman on 2008-01-10
Right click > Open with > Firefox

---

### Post by bitra on 2008-01-11
> **Paqman said:**
> Right click > Open with > Firefox

Will that make nautilus automatically opens firefox every time I double click a *.html file?

---

### Post by chewearn on 2008-01-11
Run from terminal
```
ls -l <file.html>
```

Does the file has the execute attribute?  If yes, run:
```
chmod -x file.html
```

---

### Post by Cappy on 2008-01-11
> **bitra said:**
> Will that make nautilus automatically opens firefox every time I double click a *.html file?

To make it do it everytime on all html files:

Right click on the file --> Properties --> (TAB) Open With --> Click Firefox or whatever program you want --> Close

---

### Post by peabody on 2008-01-11
AstalaVista's solution is the correct one.  If a text file has its execute bit set, nautilus asks if you want interpret the file as a shell script.  Turn it off to disable the prompt.

---

### Post by bitra on 2008-01-17
Thanks **Cappy**, **AstalaVista**. The problem has been solved.

Thanks again. :)

---


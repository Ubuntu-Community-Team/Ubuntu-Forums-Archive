---
title: "zipped archive"
date: 2007-12-01
forum: Absolute Beginner Talk
---

### Post by fmbugdadi on 2007-12-01
Is there a zip archive utility, or a command line command that will allow me to zip multiple files? IF not, where can I get an utility to do that?

thank you

---

### Post by kellemes on 2007-12-01
[7-zip]("http://www.7-zip.org/")

---

### Post by fmbugdadi on 2007-12-02
that zip utility is only available for windows... (7 zip)

---

### Post by CatKiller on 2007-12-02
What do you mean by multiple files?

File Roller (included by default) can create an archive of however many files you want. Highlight them, right-click, and select "Create Archive..." You can make zips with that.

---

### Post by fmbugdadi on 2007-12-02
Oh, I see, thanks.. Please excuse my ignorance, as I am new to Linux.....

---

### Post by niteshifter on 2007-12-02
As CatKiller said the file-roller (aka Archive Manager) will let you zip files:

Start Archive Manager.
Click New.
Enter a name for the archive.
Select .zip as the Archive type.
Drag files from any open file browser window onto the Archive Manager's window to add them to the archive.

When done adding files, Ctrl+Q quits the program (or menu Archive /  Quit) and the zip archive is saved automatically.

For the command line there's zip, as in:
```
zip myarchive.zip *
```
Will place all files in the current directory into a zip file called myarchive.zip. zip is very versatile, have a look at the man page on it. The program unzip does exactly that.

---


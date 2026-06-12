---
title: "Exporting contents listing of folder and/or zip file to text"
date: 2007-02-26
forum: Absolute Beginner Talk
---

### Post by ajifans on 2007-02-26
Bit of a strange request, but I want to list the contents and properties of a zip file, and export these to a text file or spreadsheet.

So at the end I want a file that lists the contents of a zip file or folder with the modified date for each file.

I'm thinking grep, but don't really know how to implement it in this way.

---

### Post by mcduck on 2007-02-26
For a directory, you can just run 'ls -R /path/to/your/directory/ > yourtexfile.txt' (use 'ls -lR' for more information).

edit: see 'man ls' for more output options ;)

---

### Post by ajifans on 2007-02-26
Thanks didn't think of that.  ls -g did the trick

---

### Post by mcduck on 2007-02-26
ok, and for the zip files, in the same way, 'unzip -l /path/to/archive.zip > files.txt' will do the job :)

---


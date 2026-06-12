---
title: "Endlines"
date: 2006-01-30
forum: Absolute Beginner Talk
---

### Post by Mordred on 2006-01-30
Hi

I have a lot of files with dos endlines,
how do I convert them all to unix endlines
at once?

Thanks

---

### Post by jvoegele on 2006-01-30
[QUOTE=Mordred]I have a lot of files with dos endlines,
how do I convert them all to unix endlines
at once?[/QUOTE]

First, install the package "sysutils", which contains the command "dos2unix".  You can use "dos2unix <filename>" to convert a file from CRLF to LF.

If you have a bunch of files that you want to convert, just run dos2unix on each one.  Be careful not to run dos2unix on a binary file, as it will probably corrupt the file.

---

### Post by joshuapurcell on 2006-03-22
For some reason dos2unix didn't get rid of the ^M characters in my text file which signified a return character. **vi** and sed can do this:

1. Open up the file: **vi someFile.txt**
2. Type this: **:%s/^M/\r/g** (make sure to use Ctrl-V,Ctrl-M to make the ^M sign)
3.If the file looks correct after making the change, then save it: **:wq**

---


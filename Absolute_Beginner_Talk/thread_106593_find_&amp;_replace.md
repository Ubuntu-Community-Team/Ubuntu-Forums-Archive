---
title: "find &amp; replace"
date: 2005-12-21
forum: Absolute Beginner Talk
---

### Post by Zelut on 2005-12-21
I've recently taken over web hosting for a local small business and part of the deal was that I do minor updates to the .html.  Well I've got about 100 .html pages and 90% of them have an outdated email address. (too bad more people don't use .php ehh?)

can someone tell me a shell command that can find & replace text within a file?  I vaguely think I've come across that before but I can't remember enough to piece it together.

Cheers

---

### Post by darth_vector on 2005-12-21
in vim you do:

```
:%s/oldword/newword/g
```

EDIT: sorry, i misread the question. i will see if i can dig something up :)

---

### Post by Knomefan on 2005-12-21
sed should do what you are looking for.

Handy examples:
[http://www.student.northpark.edu/pemente/sed/sed1line.txt](http://www.student.northpark.edu/pemente/sed/sed1line.txt)

---

### Post by darth_vector on 2005-12-21
```
sed 's/oldword/newword/g' filename > filename
```

will make the necessary change and overwrite the file.

---

### Post by timfrost on 2005-12-21
If you have access to perl, you can do

```

perl -pi.bak -e 's/<oldadress>/<newaddress>/' *.html

```
to change all the files in the one directory. Use of 'i.bak' in the command ensures that a backup version of each file will be created (because each original file will be renamed with a .bak suffix, and then used as input for the substitution operation).

If you have a way to build the list of source files to be editted (eg a search using grep -l), then that could restrict the affected file to those that need to be changed.  for example:
```

 perl -pi.bak -e 's/old\@add.ress/new\@addr.ess/ `find $WEBHOME -type f -print | xargs grep -l old@addr.ess`

```
which looks (using the "grep" command, which is the unix program that searches files for patterns of text) for the old address (ie "old@addr.ess") in files under the directory $WEBHOME, and generates a list of file names (the "-l" option to grep instruucts it to just print the matching file name).

The "back-quotes (`)" are treated by a unix shell as an instruction to run the command in quotes, and then place the output from that comand in the command line being run.  This means that the perl comand wlll get the list of file names that have the old address, and it will only attempt to change those files (so that it doesn't try to change a  file that doesn't have the text we want to change.

---


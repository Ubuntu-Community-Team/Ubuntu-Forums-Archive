---
title: "Bash Script convert files"
date: 2006-07-30
forum: Absolute Beginner Talk
---

### Post by walmartshopper67 on 2006-07-30
I have a bunch of .chm files that I need to convert to html. I have the program to do it - extract_chmLib. I really don't want to convert over 500 .chm files one at a time. I'm having trouble writing the script to do it. It should be simple, but I don't get the syntax for it. I don't know how to get it to traverse the directories and convert the files keeping the names the same. Is there an easy way to do that?

---

### Post by chalex on 2006-07-30
According to a quick google search, extract_chmLib takes two arguments.  The first is the name of the CHM file, the second is the name of the directory which is to contain all of the extracted files.

So suppose you have a directory full of CHM files.
$cd dir_full_of_CHM_files
$ls | xargs -I file extract_chmLib file file

That will expand each CHM file into a directory of the same name.  Then you can move the CHM files somewhere.
$mv *.chm /path/to/elsewhere/

And you'll be left with a directory full of directories which contain the contents of each CHM file.

---


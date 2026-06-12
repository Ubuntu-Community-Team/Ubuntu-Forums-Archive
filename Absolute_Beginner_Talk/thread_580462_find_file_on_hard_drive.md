---
title: "find file on hard drive"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by Sarke on 2007-10-18
OK, I'm sure this is retardedly easy, but I'm not finding any info on it.  I tried searching for the answer but the keywords in the search are everywhere so the results are not helpful.

The question is: how do I find files on a hard drive?  Like the good old *.zip searches etc.

I have installed a few search tools (like Desktop Search) but they all work on indexes from my home folder, but what I want to find is on an NTFS partitioned hard drive.

---

### Post by juan@forum on 2007-10-18
find  /ntfspartition  -name  *.zip

---

### Post by h2gofast on 2007-10-19
Click Places, 
Click computer
On the file manager window that pops up Click Go
On the drop down list click on Search for files
Enter the name or a portion of the name (case sensitive?) and hit the Enter button.
There you go.



The command line is faster once you learn a few commands.

---

### Post by Whiffle on 2007-10-19
Or, assuming your db is up to date:

locate filename 


in terminal.

---


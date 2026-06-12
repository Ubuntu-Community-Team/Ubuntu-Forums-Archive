---
title: "shell script write pi"
date: 2007-03-17
forum: Absolute Beginner Talk
---

### Post by glederfein on 2007-03-17
Hi all!
I found a program called "pi" which calculates pi to how many digits specified. 
How can I write a shell script that writes the output of the program to a text file?

---

### Post by mcduck on 2007-03-17
You don't need a script for that, the feature is built in to bash. if your program is called 'pi' and it usually outputs the data to your screen, you can just run 'pi > file.txt' and the output will be saved in a text file.

---

### Post by glederfein on 2007-03-17
> **mcduck said:**
> You don't need a script for that, the feature is built in to bash. if your program is called 'pi' and it usually outputs the data to your screen, you can just run 'pi > file.txt' and the output will be saved in a text file.
Thanks, It worked perfectly!

---

### Post by chalex on 2007-03-17
FYI, the feature is called "output redirection".

---

### Post by DaveBorealis on 2007-03-17
> **glederfein said:**
> Thanks, It worked perfectly!

As an aside, if you do anything funky with your code such as calculating pi to a million digits, you might want to save from within your script so that you have control over how it's handled.  For instance I'd probably buffer only a few thousand digits at a time if I were calculating hours' worth of data, then save it, appending it to a text file.  In Perl and Python it's easy enough to do.

Dave

---


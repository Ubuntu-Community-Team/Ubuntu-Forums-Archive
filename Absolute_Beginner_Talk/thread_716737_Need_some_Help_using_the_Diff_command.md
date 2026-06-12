---
title: "Need some Help using the Diff command"
date: 2008-03-06
forum: Absolute Beginner Talk
---

### Post by smoothcne on 2008-03-06
Hi folks, Yes Im a NOOB so I need some help here...

I am trying to troubleshoot a printing issue in my building and I have captured several packet captures and I need to compare the two different files to see why one condition works and the other doesn't. I was hoping that I could run them against the Diff command to get an output of the differences but all I get is that the two binary files differ.

Is is because they are in a binary format that Diff won't display the differences? Or is it a command issue?

---

### Post by justleen on 2008-03-06
diff wont compare binary files, no

you can try to run them through strings first though
strings file1 > file1.plain
strings file2 > file2.plain
diff file1.plain file2.plain

---

### Post by newlinux on 2008-03-06
maybe try vbindiff - according to the repos it visually compares binary files.

---

### Post by smoothcne on 2008-03-06
Hey thanks! I'll try both of those suggestions.

---


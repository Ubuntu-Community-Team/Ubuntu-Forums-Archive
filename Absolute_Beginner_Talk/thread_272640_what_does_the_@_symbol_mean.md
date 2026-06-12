---
title: "what does the @ symbol mean ??"
date: 2006-10-06
forum: Absolute Beginner Talk
---

### Post by unlokia on 2006-10-06
Hey people!. I am wondering what the "@" symbol signifies, tacked onto the end of a filename.

I have a file named "S99local" and it says "Shell Script (Link)" and when I do:

# ls

it says

S01local@

How do I rename one of these and KEEP its attributes intact??.... confused :S

Many thanks!

---

### Post by Arevos on 2006-10-06
It may mean that the file is a symbolic link. As for renaming files, you can use the "mv" command, or "sudo mv" if you want to move a file with root permissions. However, beware of renaming files with sudo if you are uncertain of what you are doing. Perhaps if you gave more information about the problem?

---


---
title: "[SOLVED] remove files via cli"
date: 2007-10-07
forum: Absolute Beginner Talk
---

### Post by ncappel1 on 2007-10-07
after having a batch file rename/case change ordeal, I finally thought I came out on top. I needed to recursively replace spaces with underscores in a directory, and also change upper to lowercase. I finally figured out how to do that (heres the thread: [http://ubuntuforums.org/showthread.php?t=206299](http://ubuntuforums.org/showthread.php?t=206299))

But now the issue that I have is that the files in the directory were not overwritten! I now have double the files I had earlier, the new ones that are nice and tidy (lowercase, underscores) and the old ones that are not. 

Is there a way to run similar commands to recursively **remove**(not replace, or rename) files that have spaces and mixed case words?

---

### Post by nick_h on 2007-10-07
Yes, use find again but test it first with the -print option, for example:
```
find -type f -name "* *" -print
```
then when you are happy with the pattern you have chosen you can replace the -print with -exec rm '{}' \;
If in doubt make a bakup first.

---

### Post by ncappel1 on 2007-10-07
yay, thanks nick_h, i used your help and finally found a solution to my problem. i used the pattern you suggested, and also *[A-Z]* to find names that had a capitol letter, everything is good again, thank you!

i'm motivated to learn more about regular expressions now, such  powerful tool!

---


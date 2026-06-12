---
title: "what does &quot;sh ./runme &quot; mean?"
date: 2007-05-16
forum: Absolute Beginner Talk
---

### Post by gotquestions on 2007-05-16
i am trying to understand what does

"sh ./runme " mean

runme - is the file
sh - i guess that is the way to run the shell script?

but what is ./ ?
would there be instances where i have to run something like:

sh ./a long/ directory/ path/ runme?

---

### Post by taurus on 2007-05-16
./ means current directory.  Since runme is not in your path, you need to tell the shell to run it in the current directory, ./.

---

### Post by FuturePast on 2007-05-16
Yes, sh is a command, and in this case the ./ is unnecessary. The dot means the path starts in the current directory.

---


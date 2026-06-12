---
title: "[SOLVED] Make error 127"
date: 2007-08-23
forum: Absolute Beginner Talk
---

### Post by yogo on 2007-08-23
Making all in po
make[1]: Entering directory `/home/naty/installs/Scribes/scribes-0.3.2.8/po'
file=`echo de | sed 's,.*/,,'`.gmo \
          && rm -f $file &&  -o $file de.po
/bin/sh: -o: not found
make[1]: *** [de.gmo] Error 127
make[1]: Leaving directory `/home/naty/installs/Scribes/scribes-0.3.2.8/po'
make: *** [all-recursive] Error 1
root@naty-desktop:/home/naty/installs/Scribes/scribes-0.3.2.8#

Any ideas, I think I have all the build essentials and other files?

---

### Post by yogo on 2007-08-23
I really do not have an answer but I thought I had everything in place and I did it again and no error. Solved

---


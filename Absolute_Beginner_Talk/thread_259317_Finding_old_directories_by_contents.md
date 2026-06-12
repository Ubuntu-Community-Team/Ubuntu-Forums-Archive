---
title: "Finding old directories by contents"
date: 2006-09-17
forum: Absolute Beginner Talk
---

### Post by sidefx on 2006-09-17
Here's a question for you all - what command could I use in the following scenario:

I have a directory with many sub directories where each subdirectory holds a number of files. Ideally I would like to print a list of the sub directories in ascending order by the last modified date of the most recently modified file within each of them. In this way I can find the "oldest" sub directories.

I imagine I can do something by piping the output of ls with R and r switchs or some such, but is there a simple way to do it on the command line?

Hope this makes sense...

ta

---

### Post by steve.horsley on 2006-09-17
Since a directory gets modified when a file is created or deleted, you may be able to make use of this. If the files in the directories are just being created, then **ls -ltr** is probably all you need. 

If the files are modified after creation, then you probably need a smallish script to rummage through finding the oldest file in each directory and then sorting the directories. You could try the following smallish script. Paste it into a file and then make the file executable:
```

#!/usr/bin/python
import os, time
dirs = []
for d in os.listdir("."):
    if os.path.isdir(d):
        t = 0
        for f in os.listdir(d):
            fname = os.path.join(d, f)
            if os.path.isfile(fname):
                t = max(t, os.stat(fname)[8])
        dirs.append((t, d))
dirs.sort()
dirs.reverse()
for t, d in dirs:
    print d, time.ctime(t)

```

---


---
title: "i know there's got to be a single command for this"
date: 2006-11-27
forum: Absolute Beginner Talk
---

### Post by Y4CcduyctJL3 on 2006-11-27
ok, need a command line guru's help here.  i need a command to create duplicates of all files in a directory hierarchy in the same directory as the original file with .bak on the end of the new files.

TIA

---

### Post by hod139 on 2006-11-27
not tested, but how about 
```

for i in `find -type f`;do  cp ${i} ${i}.bak; done

```This will create a copy of every regular file (ignores directories, links, etc) and add the extension.bak.

**EDIT:** The above code will break if you have any spaces in your filenames.  You can try this instead:
```

find -type f -print0 | xargs -0 -i cp ./{} ./{}.bak

```

---

### Post by Y4CcduyctJL3 on 2006-11-28
that's just insane!  where would i be without you people?  well i don't know yet, but i'll tell you where i won't be; chained to a desk at the corporate office of monotony in friendly downtown my-own-private-hell.  thanks allot.

---


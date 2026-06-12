---
title: "rename a file beginning with '-' in terminal"
date: 2007-01-27
forum: Absolute Beginner Talk
---

### Post by dccmyst on 2007-01-27
A noob question. 

I would like to rename a file that begins with a dash, but when I try 'mv' in the terminal it mistakes the dash as an argument. 

I dont want to use nautilus. 

(I just want to say, ubuntu is smashing! I'm kicking myself for not using *nix sooner.)

---

### Post by JamieC on 2007-01-27
Quote the filename (single or double):
```

mv "~/-myfile" "~/myfile"

```

---

### Post by kosmic on 2007-01-27
simply do :

If the file name is -test

type this in a terminal

  *** mv ./-test test***

and it should rename it :)

---


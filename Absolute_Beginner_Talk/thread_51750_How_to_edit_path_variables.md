---
title: "How to edit path variables???"
date: 2005-07-25
forum: Absolute Beginner Talk
---

### Post by grofaz on 2005-07-25
How do you add path variables to .bashrc file ??

I'm trying to set up HLA and I need to add some additional paths to the .bashrc file but I don't see where to do that ??

I'm supposed to find the following line:

"PATH=$DBROOT/bin:$DBROOT/pgm:$PATH"

And alter to:

"PATH=$DBROOT/bin:$DBROOT/pgm:/usr/hla":$PATH

The trouble is I can't find this line, it doesn't exist. So how do you set the path variables ?

Thanks!

---

### Post by charlieg on 2005-07-25
I believe the following works fine:
```
export PATH=$PATH:/some/other/dir
```

So in your case, put this in your .bashrc:
```
export PATH=$PATH:/usr/hla
```

---

### Post by grofaz on 2005-07-25
That's all, just add in the necessary code ? OK, but how are paths handled now if the code isn't in there already ? Thanks for the answer, appreciate it!

---


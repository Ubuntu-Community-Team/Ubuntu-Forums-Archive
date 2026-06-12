---
title: "Changing default permissions (again)"
date: 2006-10-14
forum: Absolute Beginner Talk
---

### Post by opticsnake on 2006-10-14
I guess maybe I must have misspoken myself when I posted before. My current default permissions are -rw-rw-rw- which the umask (22) changes to -rw-r--r-- I would like my default permissions to be -rwxrw-rw- even before the umask touches it and without me having to do a chmod every time I create a new script.

Anyone know how to change it?

Edit:
Talked to my Comp Science professor yesterday and he informed me that you can't change the default permissions.  There is no way to make it so that when you create a script it is automatically executable.  You can pass the value "766" to a script when using the open() system call, however, which will make the new file it creates executable.

---

### Post by David_T on 2006-10-14
Hmm. I don't know, but it seems like it might be a better idea to create a script and put it in /usr/local/bin, and call it something like ns for newscript:
```

#!/bin/bash
touch $1 && chmod 755 $1 && vi $1

```

---

### Post by Blagomir on 2006-10-14
Why don`t you try umask 222 instead of 22 ?

---


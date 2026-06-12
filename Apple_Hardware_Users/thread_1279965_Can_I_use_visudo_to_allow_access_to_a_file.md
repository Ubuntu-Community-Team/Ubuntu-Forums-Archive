---
title: "Can I use visudo to allow access to a file?"
date: 2009-10-01
forum: Apple Hardware Users
---

### Post by mrcoulson on 2009-10-01
I understand I can use visudo to allow a user to perform a command without password.

myuser ALL=NOPASSWD:/come/command

I want to do the same thing with a file.  I have an AppleScript that is supposed to copy some files and I want it to happen without asking for a password.  Can I use visudo like this?

I know it's not a totally UBUNTU question, but I'm pretty sure that you guys know the answer anyway!

Jeremy

---

### Post by mrcoulson on 2009-10-01
I've given my user the ability to use cp without a password.  Can I limit that to just one directory?  

Jeremy

---

### Post by sisco311 on 2009-10-01
Why don't you change the permissions of the destination folder?

Or you could write a little script:
```

#!/bin/sh
cp $1 /path/to/dest

```

usege: scriptname filename
and add it to the sudoers file:
```
myuser ALL=NOPASSWD: /path/to/script
```
NOTE: make sure that the script is owned by root:root and it's **not** writable by others.

or try something like:
```
myuser ALL=NOPASSWD: /bin/cp * /path/to/dest
```

[HowTO: Sudoers Configuration]("http://ubuntuforums.org/showthread.php?t=1132821")

---


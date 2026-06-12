---
title: "Command line help"
date: 2007-09-02
forum: Absolute Beginner Talk
---

### Post by detroit/zero on 2007-09-02
I'm having trouble structuring a command. I've read the help and man pages for *chmod* but I can't seem to get it quite right.

I've backed up a number of files from an Ubuntu laptop onto an Ubuntu  desktop computer using *ssh* and *scp* commands. Without thinking, I prefixed all my copy-file commands with *sudo*, and now all the files/folders/directories that I copied are root-access only.

Basically, what I'm trying to do is change the permissions on **all** files and folders in my home directory back to my user-group and me as a user.

Going through and doing a *right-click> properties> permissions* and changing each individual file, folder, and archive got old after the first 5 minutes.

Would someone mind showing me the error of my ways?

---

### Post by CRCarl on 2007-09-02
```
chown -R <username> *
chgrp -R <username> *
```

---

### Post by Paul133 on 2007-09-02
What CRCarl said. I didn't realize the group name is the same as the user name.

---

### Post by detroit/zero on 2007-09-02
That was fast.

Worked like a charm. Thank you.

---


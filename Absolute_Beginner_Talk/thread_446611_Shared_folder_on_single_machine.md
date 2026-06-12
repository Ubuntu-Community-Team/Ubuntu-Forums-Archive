---
title: "Shared folder on single machine"
date: 2007-05-17
forum: Absolute Beginner Talk
---

### Post by jimcooncat on 2007-05-17
I want to share a folder with different users on the same machine, for example: /home/shared

When someone copies a file into the folder, I want everyone in the "shared" group to have read and write access to it.

I'd prefer that the "file owner" remains the same so we know who contributed the file.

How best to implement this? Setgid on the directory? Change the umask? Definitely, I need help as an Absolute Beginner on this topic.

---

### Post by FuturePast on 2007-05-17
$ sudo addgroup sharers
$ sudo mkdir /home/shared
$ sudo chgrp sharers /home/shared
$ sudo chmod g+s /home/shared
$ sudo adduser jim sharers

I'm not sure about the umask part. 
You might need to change that so the files created in the dir have group write access.

---

### Post by ubnewbie2 on 2007-05-17
> **FuturePast said:**
> $ sudo addgroup sharers
$ sudo mkdir /home/shared
$ sudo chgrp sharers /home/shared
$ sudo chmod g+s /home/shared
$ sudo adduser jim sharers

I'm not sure about the umask part. 
You might need to change that so the files created in the dir have group write access.

Mine is u=rwx,g=rx,o=rx by default, and 
```

 umask -S u=rwx,g=rwx,o=rx
```

will set it to make files r/w by group members

---

### Post by jimcooncat on 2007-05-17
thanks!

I'll test that if things get a little quieter here. I'm curious if it will work the way I want if I:

copy a single file to it
copy a whole directory to it

---


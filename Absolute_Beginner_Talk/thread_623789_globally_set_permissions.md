---
title: "globally set permissions"
date: 2007-11-26
forum: Absolute Beginner Talk
---

### Post by davidexe on 2007-11-26
I cannot find this in search.. I am setting up a server and have it about done, EXCEPT,  the folders in the server come up without write permission.  I have set the upper folders to that permission but that does not change the folders within. 

How do I globally set all of the folders to have writer permission?

Thanks.

---

### Post by hyper_ch on 2007-11-26
use the -r option which means "recursive"

---

### Post by davidexe on 2007-11-26
I am using the GUI and do not know the proper format for the permissions setting for the line command.  Is there a way in the GUI or can you give me the general format for the permissions line command?

Thanks.

---

### Post by hyper_ch on 2007-11-26
the command is called "chmod"

```

sudo chmod -R 0755 /path/to/dir

```

Where 0755 is the rights you give the folder and it subfolders/files

---

### Post by davidexe on 2007-11-26
THANKS

Got it all working..

---


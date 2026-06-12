---
title: "Permissions"
date: 2007-09-12
forum: Absolute Beginner Talk
---

### Post by codeking on 2007-09-12
I'm trying to install a new theme, but the folder I need to transfer the file to always shows up errors because I don't have permission to write to the folder.  How do I change the permissions?

---

### Post by Celegorm on 2007-09-12
Try putting ```
sudo mv /path/to/file /path/to/folder/you/want/it/in
``` in the terminal (applications->accessories->terminal if you haven't used it before). Press enter and it will ask for you password, which will not be echoed to the screen- this is normal.

---

### Post by Gerard Barberi on 2007-09-12
Changing permissions: [http://www.ss64.com/bash/chmod.html](http://www.ss64.com/bash/chmod.html)
 
In case you need to change the owner of the folder:
[http://www.ss64.com/bash/chown.html](http://www.ss64.com/bash/chown.html)

---


---
title: "batch file"
date: 2006-02-24
forum: Absolute Beginner Talk
---

### Post by seekyrr on 2006-02-24
I would like to make this command into a clickable icon on the desk top.  What extension should I save it as to run?  Also can sudo be included and propt for a password to run it?

example.

/opt/nessus/sbin/nessus-update-plugins


Thanks

Seeky

---

### Post by gsdefender on 2006-02-24
You don't need any special extension. You only need to prepend

```

#!/bin/bash

```

or whatever shell you want to be used as parser to the script file, and then add a link to this:

```

gnome-terminal --command /full/path/to/your/script

```

Should you ever need root privileges, invoke the script using

```

gksudo gnome-terminal --command /full/path/to/your/script

```

Hope this helps.

---

### Post by seekyrr on 2006-02-24
Ty..but I seem to be missing something basic.

With text editor I made a file called update.

#!/bin/bash
gnome-terminal --command /opt/nessus/sbin/nessus-update-plugins


Problem is, if I double click on it..it just opens in text editor.

Thanks

Seeky

---

### Post by auburn on 2006-02-24
and make the script executable:
```
chmod +x filename

```

if you want (not necessary) you can give a bash script a .sh extension, but it's only a naming convention.

---

### Post by auburn on 2006-02-24
If I didn't want the terminal to come up, is there a way to do that?

---

### Post by xhie on 2006-02-24
you dont need the whole gnome-terminal --command part, 
just whatever command your trying to execute. 

chmod +x scriptname after your done and set a starter to the whole thing, or whatever it was you wanted to do.

---

### Post by seekyrr on 2006-02-24
Thanks everyone..working good now!

Seeky

---


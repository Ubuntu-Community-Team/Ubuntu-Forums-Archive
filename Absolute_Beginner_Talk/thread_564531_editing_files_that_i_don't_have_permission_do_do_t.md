---
title: "editing files that i don't have permission do do that"
date: 2007-10-01
forum: Absolute Beginner Talk
---

### Post by Peter Alien on 2007-10-01
Sometimes i need to edit some files, but i don't have permission over them.

I can edit them by putting it's path in the Console, but can anyone tell me how can i have permissons to those files in Nautilus (it's more easy to get to them than in Console)?


Many thanks

---

### Post by nickpaton on 2007-10-01
To open Nautilus

```
gksudo nautilus
```

But what sort of files are you wanting to edit, because there may be easier and certainly safer ways to do it.

---

### Post by Prometheus7 on 2007-10-01
you use the command chmod in the terminal to change the permissions of a file or directory...

chmod ### name_of_file

where # = a number from 0 to 7 representing the privilege.

chmod 777 makes the file read/write/executable by anyone, for example,
chmod 755 makes it read/write/exec by root and only read/write by anyone else

[http://www.ss64.com/bash/chmod.html](http://www.ss64.com/bash/chmod.html)

you should read up on groups as well.

---

### Post by 1337455 10534 on 2007-10-03
Umm, you Kubuntu?? Hmm:
This is how I would do it in GNOME..
```

gksudo gedit /asd/fgh/jkl

```

---


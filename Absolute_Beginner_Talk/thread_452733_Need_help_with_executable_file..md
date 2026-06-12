---
title: "Need help with executable file."
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by adt41287 on 2007-05-23
i want to make an executable file that will change directory to "/media/sda1/dvdrip" and run the command "vobcopy -m" but i do not know where to start.  I eventually want to make a launcher on my desktop to run this command. Does anybody know of any good 'how to's' out there or any suggestions??. thanks in advance!

---

### Post by wpshooter on 2007-05-23
Don't you mean that you want to make a script (or as in old DOS language, BATCH file) to accomplish these tasks ?

If so, why don't you do a search on the forums on script language or google on Linux scripts.

---

### Post by annda on 2007-05-23
highly recommended:
[http://linuxcommand.org/writing_shell_scripts.php](http://linuxcommand.org/writing_shell_scripts.php)

read the whole thing, not only the part about shell scripting.

---

### Post by Cypher on 2007-05-23
So..
```

#!/usr/bin/env sh

DIR="/media/sda1/dvdrip"
CMD="vobcopy -m"

cd $DIR && $CMD

```

---

### Post by adt41287 on 2007-05-23
thanks wpshooter and annda, ill check it out

---

### Post by adt41287 on 2007-05-23
> **Cypher said:**
> So..
```

#!/usr/bin/env sh

DIR="/media/sda1/dvdrip"
CMD="vobcopy -m"

cd $DIR && $CMD

```

what extension do i use??

---

### Post by Cypher on 2007-05-23
What I usually do for the these things is create a directory called "bin" in your home directory, add that directory your path. Then create this file, you can add ".sh" extention if you want to know it's a SHell script.

Then
```

chmod 755 <file>.sh

```

---

### Post by adt41287 on 2007-05-23
awesome!! thanks Cypher ... its up and running... thanks again

---

### Post by Cypher on 2007-05-23
Your welcome and happy Ubuntu'ing..:)

---

### Post by phr0ze on 2007-05-23
> **adt41287 said:**
> what extension do i use??

Linux doesn't need extensions to identify executable files. They are sometimes used to help the user, but its the chmod command that really makes it executable.

---


---
title: "How do I install a package??"
date: 2006-07-24
forum: Absolute Beginner Talk
---

### Post by denfoote on 2006-07-24
I have a package installed on my desk top.
It's a TAR GZ package.
How do I install it!!
I'm going nutz trying to figure this out!!
I need somebody to talk me through it. Then I'll know how to do it the next time.
Thanks.

---

### Post by Jagot on 2006-07-24
[http://www.monkeyblog.org/ubuntu/installing/#source](http://www.monkeyblog.org/ubuntu/installing/#source)

Make sure the package you're trying to install is not in Ubuntu's repositories first though.

---

### Post by underdog512 on 2006-07-24
open a terminal and use the tar command on the package 

type "man tar" for more info.

---

### Post by underdog512 on 2006-07-24
Take a look at these sites as well.  This should offer alot of help.  

[https://help.ubuntu.com/ubuntu/desktopguide/C/add-applications.html](https://help.ubuntu.com/ubuntu/desktopguide/C/add-applications.html)

[https://help.ubuntu.com/ubuntu/desktopguide/C/synaptic.html](https://help.ubuntu.com/ubuntu/desktopguide/C/synaptic.html)

ps  synaptic is really cool

---

### Post by Sef on 2006-07-24
What package are you trying to install?

---

### Post by denfoote on 2006-07-25
Avast4 work station for Linux.

Anti virus program.

I may not need it, but I feel safer having it.
I have just migrated over from Windows!! ;)

---

### Post by Perfect Storm on 2006-07-25
Try search our howto section for anti-virus then. I wrote two diffrent ones.

---

### Post by sebz2005 on 2006-07-25
This could help:

Open a terminal and do the following:
```

sudo -s

<type password here>

cd /path/to/file/
tar -xvjf (file).tar.gz
cd (file)
./configure
make
make install
``` 
Replace (file) with the file name without the '.tar.gz', and /path/to/file/ with the localtion, eg. /home/sebz/Desktop

---


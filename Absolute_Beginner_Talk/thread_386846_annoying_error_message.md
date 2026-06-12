---
title: "annoying error message"
date: 2007-03-17
forum: Absolute Beginner Talk
---

### Post by noob_saioke45601 on 2007-03-17
hey all, everything i install i always get this message.

```
Setting up sun-java5-doc (1.5.0-08-0ubuntu1) ...
This package is an installer package, it does not actually contain the
J2SDK documentation.  You will need to go download one of the
archives:

    jdk-1_5_0-doc.zip jdk-1_5_0-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    http://java.sun.com/j2se/1.5.0/download.html

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort] 

```

i press enter and it pops up again. i always have to type no twice then itwill proceed. sometimes the program wont even install cause of it or if it does it has no sound or somthing. i downloaded the jdk doc file to my desktop but no dea where to put it. i notice it should be owned by root.root and copied to /tmp so how do i do that?

---

### Post by ArieT on 2007-03-17
Login as root. Copy the zip file towards /tmp:
```

mv loc/name.zip /tmp/

```
Or start the file manager as root.

---

### Post by qpwoeiruty on 2007-03-17
You don't need to be root. After moving it, just:

```

chown root /tmp/name.zip
chgrp root /tmp/name.zip

```

---

### Post by noob_saioke45601 on 2007-03-17
> ArieT  	Login as root. Copy the zip file towards /tmp:
Code:

mv loc/name.zip /tmp/

Or start the file manager as root.

thanks that helped.

---


---
title: "php problem"
date: 2006-06-12
forum: Absolute Beginner Talk
---

### Post by finch on 2006-06-12
I take apache2 / php5 / sql on Ubuntu 5.10
using instructions [here]("https://wiki.ubuntu.com/ApacheMySQLPHP")
When load [http://localhost/test.php](http://localhost/test.php)
[IMG]http://phpinfo.free.bg/Screenshot.png[/IMG]
 i also install phpbb forum and he works..

What to do ?
Thx in advance

---

### Post by fluffington on 2006-06-12
It looks like Apache doesn't have permission to read test.php. Making it world-readable aught to fix the issue.

```
chmod a+r /var/www/test.php
```

---

### Post by finch on 2006-06-12
ye .. it works, but how to make all files readable?
thx

---

### Post by fluffington on 2006-06-12
I'm not entirely sure I understand what you're asking, so if this doesn't answer it, you probably need to rephrase the question.


You can do the following to make everything in /var/www world-readable:

```
chmod -R a+r /var/www/
```

---

### Post by finch on 2006-06-12
I want to all old and new created files in /var/www/ ot make readable automaticaly.
Can i ?
thx

---

### Post by fluffington on 2006-06-13
The command I posted previously will set permissions for all pre-existing files. As for new files, I don't know the specifics (never used it myself), but I think the [umask](http://www.die.net/doc/linux/man/man1/umask.1.html) command may be what you're looking for.

---


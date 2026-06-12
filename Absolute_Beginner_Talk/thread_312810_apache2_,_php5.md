---
title: "apache2 , php5"
date: 2006-12-05
forum: Absolute Beginner Talk
---

### Post by pavel_kbc on 2006-12-05
Warning: Unknown: failed to open stream: Permission denied in Unknown on line 0

Warning: Unknown: Failed opening '/var/www/index.php' for inclusion (include_path='.:/usr/share/php:/usr/share/pear') in Unknown on line 0

what i do now???

---

### Post by pavel_kbc on 2006-12-05
here is the code of  /var/www/index.php
[PHP]<?php phpinfo(); ?>[/PHP]

---

### Post by Voxxi on 2006-12-05
You have a permissions problem. Apache can't access the file, as it is not owned by root. Try putting in the command line:

```
chmod 744 /var/www/index.php
```

That changes the permissions so Apache can read the file. ;)

EDIT: I thought I might provide some more information on chmod.

Chmod stands for **ch**ange **mod**e. What it does is change the permissions (Or "mode") of a file. File permissions dictate who can read, write to and execute a file. The numbers after chmod represent the new file permissions. The first number represents the permissions of the "owner", i.e the person who created the file. The second number represents the permissions of the "group", i.e the group the user who created the file belongs to. The third number represents everyone else.

The numbers are a bit complicated. Let me how you:

Read = 4
Write = 2
Execute = 1

So, say I wanted to have a permission which has read & write, but no execute. I would add up all the numbers: 4 + 2 = 6.

This might be a bit hard to understand, but it's a very valuable skill to learn. [Here]("http://www.psychocats.net/ubuntu/permissions") is some more information if you need it.

---

### Post by pavel_kbc on 2006-12-05
wow thank you its working :)

EDIT: thank your for chmod information

---


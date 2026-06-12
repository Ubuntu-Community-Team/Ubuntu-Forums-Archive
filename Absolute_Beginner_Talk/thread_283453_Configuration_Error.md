---
title: "Configuration Error"
date: 2006-10-24
forum: Absolute Beginner Talk
---

### Post by dboyer02 on 2006-10-24
Seemingly unable to get Ubuntu Server 6.06 configured properly (all I really wanted was a LAMP server) I did a clean install of Ubuntu 6.06. I once again carefully followed the community instructional article on adding and configuring Apache2, Mysql, and PHP5. Checking each step of the way everything seems to be working correctly, yet when I try to open a test.php file I get:

Warning: Unknown: failed to open stream: Permission denied in Unknown on line 0
Warning: Unknown: Failed opening '/var/www/test.php' for inclusion (include_path='.:/usr/share/php:/usr/share/pear') in Unknown on line 0

Can someon tell me what's stillnot configured correctly?
Many thanks!

---

### Post by lreyes6 on 2006-10-24
>  Warning: Unknown: failed to open stream: Permission denied in Unknown on line 0

try this at the console... ```
sudo chmod 755 /var/www/test.php
```

and try again.... this will set the normal permissions for a php file (755)

---

### Post by dboyer02 on 2006-10-24
That did the trick! Thank you!

---

### Post by lreyes6 on 2006-10-24
Great!! It's allways recomended to chmod 755 all the php files so the webserver has read permission over them

:D

---


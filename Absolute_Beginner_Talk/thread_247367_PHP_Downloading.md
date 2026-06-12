---
title: "PHP Downloading"
date: 2006-08-30
forum: Absolute Beginner Talk
---

### Post by ChestRockwell on 2006-08-30
Hello,

Not sure exactly what happened, but Apache is no longer serving up PHP pages.  I tried restarting apache with the apache2 -k restart command and that didn't do anything.  I have made sure that

AddType application/x-httpd-php .php
AddType application/x-httpd-php-source .phps

those two lines are uncommented in my apache2.conf file and i restarted apache again, but its still NOT serving up the pages.  I have ALSO deleted Apache AND PHP and reinstalled both of them but its STILL not working.  I am really lost now.  Not a clue why this isn't working.  HELP!

---

### Post by Kurt` on 2006-08-30
This thread is probably better off in [Server Talk](http://ubuntuforums.org/forumdisplay.php?f=45). Maybe a moderator can move it there.

Not sure about your problem, but after doing a configuration change, use:

# sudo /etc/init.d/apache2 reload

to reload your config files. If you need to restart apache:

# sudo /etc/init.d/apache2 restart

Good luck!

---


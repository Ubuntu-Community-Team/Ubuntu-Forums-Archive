---
title: "phpMyAdmin Permission problems in 7.04"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by fleet on 2007-10-18
Installed phpMyAdmin on Feisty through the Package Manager. php works as does appache and Mysql. 

However when I run phpMyAdmin I get the following errors. I have looked at similar posts and it seems phpMyAdin does not sit so well on Feisty. 

Warning: Unknown: open(/var/lib/php5/sess_O4iwfGCk0v6R9ZELRiCI2cP,P-9, O_RDWR) failed: Permission denied (13) in Unknown on line 0

Warning: Unknown: Failed to write session data (files). Please verify that the current setting of session.save_path is correct (/var/lib/php5) in Unknown on line 0

The error log shows a missing file: 

[Thu Oct 18 20:04:25 2007] [notice] Apache/2.2.3 (Ubuntu) PHP/5.2.1 configured -- resuming normal operations
[Thu Oct 18 20:12:35 2007] [error] [client 127.0.0.1] File does not exist: /var/www/phpmyadmin/favicon.ico
[Thu Oct 18 20:12:35 2007] [error] [client 127.0.0.1] File does not exist: /var/www/phpmyadmin/favicon.ico
[Thu Oct 18 20:12:35 2007] [error] [client 127.0.0.1] File does not exist: /var/www/phpmyadmin/favicon.ico
[Thu Oct 18 20:12:45 2007] [error] [client 127.0.0.1] File does not exist: /var/www/phpmyadmin/favicon.ico
[Thu Oct 18 20:12:46 2007] [error] [client 127.0.0.1] File does not exist: /var/www/phpmyadmin/favicon.ico
[Thu Oct 18 20:12:46 2007] [error] [client 127.0.0.1] File does not exist: /var/www/phpmyadmin/favicon.ico
[Thu Oct 18 20:12:50 2007] [error] [client 127.0.0.1] File does not exist: /var/www/phpmyadmin/favicon.ico
[Thu Oct 18 20:13:00 2007] [error] [client 127.0.0.1] File does not exist: /var/www/phpmyadmin/favicon.ico
[Thu Oct 18 20:13:01 2007] [error] [client 127.0.0.1] File does not exist: /var/www/phpmyadmin/favicon.ico
[Thu Oct 18 20:13:01 2007] [error] [client 127.0.0.1] File does not exist: /var/www/phpmyadmin/favicon.ico
[Thu Oct 18 20:13:30 2007] [error] [client 127.0.0.1] File does not exist: /var/www/phpmyadmin/favicon.ico
[Thu Oct 18 20:13:38 2007] [error] [client 127.0.0.1] File does not exist: /var/www/favicon.ico
[Thu Oct 18 20:13:42 2007] [error] [client 127.0.0.1] File does not exist: /var/www/favicon.ico
[Thu Oct 18 20:13:43 2007] [error] [client 127.0.0.1] File does not exist: /var/www/favicon.ico

---


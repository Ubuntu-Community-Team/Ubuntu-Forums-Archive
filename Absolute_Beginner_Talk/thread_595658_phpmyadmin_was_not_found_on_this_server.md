---
title: "phpmyadmin was not found on this server"
date: 2007-10-29
forum: Absolute Beginner Talk
---

### Post by herbnet on 2007-10-29
1st,  [http://localhost/](http://localhost/) returns the Index of page with apache2-default and when clicked on states "It works!"  

2nd, installed 7.10 desktop.

3rd, mysql -p ping and status options say everything is good.

4th, sudo apt-get install phpmyadmin states the latest version is loaded.

5th, ls /var/www command shows just apache2-default

6th, [http://localhost/pcpmyadmi](http://localhost/pcpmyadmi) gets the subject line message and this: "Apache/2.2.4 (Ubuntu) PHP/5.2.3-1 ubuntu6 Server at localhost Port 80."

What's my problems/solutions, PLEASE:confused:

---

### Post by greenlegacy on 2007-10-29
Is php working correctly?
Put this in a file called test.php in /var/www/ and try viewing it with a browser:
```

# test.php
<?php phpinfo(); ?>

```

Also, I'm not sure if you used a tutorial, but this one is pretty good:
[http://www.howtoforge.com/ubuntu_debian_lamp_server]("http://www.howtoforge.com/ubuntu_debian_lamp_server")

---


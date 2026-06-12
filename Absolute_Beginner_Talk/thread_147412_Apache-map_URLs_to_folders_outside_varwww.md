---
title: "Apache-map URLs to folders outside /var/www/"
date: 2006-03-20
forum: Absolute Beginner Talk
---

### Post by linux-beginner on 2006-03-20
hello,

In apache2.
I can't map urls to folders outside /var/www/. If I type for example```
http://localhost/peter/php/test.php
```
I get on the screen:
```
Not Found

The requested URL /home/mehdi/php/test.php was not found on this server.
Apache/2.0.54 (Ubuntu) PHP/5.0.5-2ubuntu1.2 Server at localhost Port 80
```

Could you say me please what I must do for this problem?
I have to say that I've made the file "alias" with: ```
sudo gedit /etc/apache2/conf.d/alias
```

Thanks,

---

### Post by dermotti on 2006-03-20
Hmm been awhile since i used apache


try [http://localhost/](http://localhost/)**~**peter/php/test.php

---

### Post by gnu2tux on 2006-03-20
You'll need to set up virtualhosts in the /etc/apache2/sites-enabled/default file

there should be a virtualhost example in there.

Regards,

Allybally.

---


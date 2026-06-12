---
title: "mini web server for testing php pages"
date: 2006-08-06
forum: Absolute Beginner Talk
---

### Post by frrobert on 2006-08-06
Is there a mini webserver package with mysql and php on it, like Easyphp (windows) that I can run on my laptop?  I do development work in php and would be able to view pages without uploading them.

thanks,

Fr. Robert

---

### Post by kebes on 2006-08-06
I do similar things, but instead of a "mini" webserver I just use the full webserver. That is, I have apache, php, and MySQL all installed. I have a symlink in my "/home" to a sub-directory of the "/var/www/html" structure, so that I can easily work on the php code. Then I have a web-browser that is pointed to:
[http://127.0.0.1/whatever/](http://127.0.0.1/whatever/)

so that I can refresh and see changes. You don't even have to be connected to the Internet for this to work: everything is local.

In linux it's easy enough to install a webserver, so I would just go ahead and do it. If your firewall is blocking port 80 then no one else will be able to see what you're working on, so there's no danger there.

---

### Post by Ryan H on 2006-08-06
If you don't want to install and configure it yourself, I suggest you use Xampp. I belive it is avaible in the repositories.

-Ryan H

---

### Post by frrobert on 2006-08-06
Thanks,

XAmpp is up and running.

Fr. Robert

---


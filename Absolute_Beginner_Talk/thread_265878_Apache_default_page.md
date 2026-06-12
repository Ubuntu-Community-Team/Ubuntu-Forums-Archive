---
title: "Apache default page"
date: 2006-09-26
forum: Absolute Beginner Talk
---

### Post by linux-beginner on 2006-09-26
Hello,

Could you say me how I can change the Apache default page from /var/www to /home/linux-beginner?

Thanks,
L-B

---

### Post by linux-beginner on 2006-09-26
By default the directory for apache server pages is /var/www, how can I change it to /home/linux-beginner?

---

### Post by po0f on 2006-09-26
linux-beginner,

Change the DocumentRoot setting in the config file.  It should be located at /etc/apache2/httpd.conf, unless Debian/Ubuntu put it somewhere else.  You'll want to edit it as root, so:
```
$ sudo gedit /etc/apache2/httpd.conf

```
should do it.

---


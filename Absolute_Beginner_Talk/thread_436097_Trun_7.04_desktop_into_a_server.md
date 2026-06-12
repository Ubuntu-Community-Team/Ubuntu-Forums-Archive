---
title: "Trun 7.04 desktop into a server"
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by proxima estacion on 2007-05-07
Hi, Got feisty going...now i want to get effectivly  a LAMP server going, but i dont want to use fesity server as i only just got fesity working!!!

I hear i can just add the components - Apache, MySQL and php...how? I see plenty of guides for edgy but none for feisty?

Help or a link to faq would be great...thx all...:)

---

### Post by pizzutz on 2007-05-07
from the terminal

```
sudo apt-get install apache2 mysql-server php5
```

edit:  once they are installed, you should be able to follow the server documentation to set them up
[https://help.ubuntu.com/6.10/ubuntu/serverguide/C/httpd.html](https://help.ubuntu.com/6.10/ubuntu/serverguide/C/httpd.html)          for Apache
[https://help.ubuntu.com/6.10/ubuntu/serverguide/C/php5.html](https://help.ubuntu.com/6.10/ubuntu/serverguide/C/php5.html)           for PHP
[https://help.ubuntu.com/6.10/ubuntu/serverguide/C/databases.html](https://help.ubuntu.com/6.10/ubuntu/serverguide/C/databases.html)  for Mysql

Those are the help pages for edgy, but to my knowledge everything there should work just fine for feisty.  Most configuration will be done through the terminal. Post any specific problems you have here. 

Happy serving! :)

---

### Post by zvacet on 2007-05-07
**synaptic>edit>mark by task>LAMP**

---

### Post by Nythain on 2007-05-07
all the above mentioned ways... but if you are that new to ubuntu/linux in general you might want to do some heavy reading before diving into a lamp server configuration... just my opinion

---

### Post by proxima estacion on 2007-05-08
> **Nythain said:**
> all the above mentioned ways... but if you are that new to ubuntu/linux in general you might want to do some heavy reading before diving into a lamp server configuration... just my opinion

Thanks, yeah I have used a WAMP server for a while but am new to Linux, so I only half know what Im doing...cheers for the tips and links :) :)

---


---
title: "server errors?? =["
date: 2008-04-07
forum: Absolute Beginner Talk
---

### Post by RadiationHazard on 2008-04-07
Ok, so I've added a proxy to my site and i keep getting the error ```
Fatal error: Call to undefined function curl_init() in /var/www/1/index.php on line 15

```

what do i do??

---

### Post by tamoneya on 2008-04-07
post the contents of /var/www/1/index.php

---

### Post by RadiationHazard on 2008-04-07
well i'm at work
but i found the package on google yesterday night
it's the Zelune Proxy if you feel like downloading it and looking/posting the index on here
i'm not able to post it on here as of right now...

---

### Post by pseudo-random on 2008-04-07
Curl support is not enabled on your server by the looks of it. You can find out with:
```

<?php
phpinfo();
?> 
```
Just load that page and search for curl to find out...

---

### Post by RadiationHazard on 2008-04-07
i'm sure that it's not
how might i go about enabling it?

---

### Post by pseudo-random on 2008-04-07
If its your server: 
```
sudo apt-get install php4-curl
```
If its not your server, open your email client and type:
Dear admin,
I would like to use curl support on my website. I notice you don't offer curl support. Please could...etc etc.

---

### Post by RadiationHazard on 2008-04-07
it's for my server
so that's all that I have to do?
:)

---

### Post by tamoneya on 2008-04-07
curl_init is defined by PHP in the cURL library.  My only guess is that you dont have this library installed correctly.

---

### Post by RadiationHazard on 2008-04-07
ok well i installed it but it's still giving me the same error
how do i refresh the server?

---

### Post by jkeyes0 on 2008-04-07
> **RadiationHazard said:**
> ok well i installed it but it's still giving me the same error
how do i refresh the server?

Once you installed it, did you restart apache? I think you can do that this way: 

```
sudo /etc/init.d/apache2 restart
```

---


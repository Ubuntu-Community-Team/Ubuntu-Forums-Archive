---
title: "Move &quot;/var/www/phpmyadmin&quot;"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by LoicNyssen on 2007-03-13
Hi,

I just wanted to know if it was possible to move the "phpmyadmin" folder to something like "/home/<username>/public_html/phpmyadmin" 

I tried just to copy it, but I get a permission denied message... 

Could someone please help

Cheers

Loic

---

### Post by DaveyG on 2007-03-14
Go to Aplications > Accessories > Terminal then type 

```

sudo gpasswd -a <user> www-data
sudo chgrp -R www-data /var/www
sudo chmod -R g+w /var/www
```

change <user> to your username, log off then log in again, then you should be able to move files & from the www folder :) 

Davey

---

### Post by LoicNyssen on 2007-03-14
I did that, copied it, but then i got a message 

```
Forbidden

You don't have permission to access /phpmyadmin/ on this server.

Additionally, a 403 Forbidden error was encountered while trying to use an ErrorDocument to handle the request.
```

---

### Post by DaveyG on 2007-03-14
Im sorry i dont know much about phpmyadmin..

but can you now move files from the /var/www folder?

---

### Post by timstl on 2007-07-31
did you ever get this figured out? i can't seem to simply move the folder.

edit: nevermind. the problem was i had apache configured to not follow sym links

---


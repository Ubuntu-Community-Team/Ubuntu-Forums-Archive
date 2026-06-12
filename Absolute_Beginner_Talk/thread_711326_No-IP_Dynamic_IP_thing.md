---
title: "No-IP Dynamic IP thing"
date: 2008-02-29
forum: Absolute Beginner Talk
---

### Post by Liesmith Loki on 2008-02-29
Hello. I'm kind of new at Linux, and I'm trying to run No-IP so I can keep a handle on the Dynamic IP thing that comes with having a router.

Well, I installed No-IP fine, but when I follow the url: [http://alkahest.no-ip.info](http://alkahest.no-ip.info), it gives me the standard "Unable to Connect" page. Same thing if I just use the Dynamic IP itself. I'm thinking this is because I need to configure either my router, or my Ubuntu to allow the world to access my /var/www folder. 

Does anyone know what I should do?

---

### Post by lespaul_rentals on 2008-02-29
Forward port 80 to your webserver's IP address.

---

### Post by steveneddy on 2008-02-29
.

---

### Post by lswest on 2008-02-29
well, on your computer there should be a httpd.conf file (not sure where it is in Linux, but you can search for it) and within that file you can find a line that looks like ```

    #
    # Controls who can get stuff from this server.
    #
#   onlineoffline tag - don't remove
    Order Deny,Allow
    Allow from all
    Allow from 127.0.0.1
```
just for you it should say Deny from All, and that has to be changed to Allow, then it should work.  good luck^^

---

### Post by Liesmith Loki on 2008-02-29
> **lswest said:**
> well, on your computer there should be a httpd.conf file (not sure where it is in Linux, but you can search for it) and within that file you can find a line that looks like ```

    #
    # Controls who can get stuff from this server.
    #
#   onlineoffline tag - don't remove
    Order Deny,Allow
    Allow from all
    Allow from 127.0.0.1
```
just for you it should say Deny from All, and that has to be changed to Allow, then it should work.  good luck^^

I found httpd.conf in /etc/apache2, but it's blank except for where I added the line "ServerName: localhost" earlier. Should I just write those things in?

---

### Post by Liesmith Loki on 2008-02-29
Nevermind. It appears, the new configuration file is apache2.conf, and httpd.conf is now a type of import file that it reads extra configurations from. I edited it in apache2! Thank you for your help! =]

---

### Post by lswest on 2008-02-29
no problem, glad i could help, sorry i got the filename wrong, i was using WAMP server 5.0 at the time and assumed it to be the same :P

---


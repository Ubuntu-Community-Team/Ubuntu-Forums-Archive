---
title: "Unzip to admined folder?"
date: 2005-09-30
forum: Absolute Beginner Talk
---

### Post by hansoffate on 2005-09-30
How do i unzip (its php-nuke.zip) to my var/www/ folder.  It is password protected.  What do i do?

---

### Post by Perfect Storm on 2005-09-30
sudo unzip php-nuke.zip var/www/

---

### Post by hansoffate on 2005-09-30
hans@hans:~/Internet_downloads$ sudo unzip PHP-Nuke-7.8.zip /var/www/ Archive:  PHP-Nuke-7.8.zip
caution: filename not matched:  /var/www/

seems not to be working

---

### Post by Perfect Storm on 2005-09-30
You sure that there is a /www in /var ?
If there isn't

```

cd /var
sudo mkdir www

```

---

### Post by hansoffate on 2005-09-30
Yeah i am sure, I already got a website hosted in that directory.  I just want to now try hosting a php-nke website.

---

### Post by Perfect Storm on 2005-09-30
Funny, I tried the out myself. No problem there. Then I tried to /var/www to test it further it wouldn't.

The command works other places but not there, can anyone come up with an explaination?

---

### Post by hansoffate on 2005-09-30
Yeah it blows my mind.... how will I get a php web portal in there?

---

### Post by hansoffate on 2005-09-30
Bump... anybody... or where can i post this for a more indepth look?

---

### Post by Perfect Storm on 2005-10-01
Okay I found out.

```

cd /where/the file/is
sudo unzip -u PHP-Nuke-7.8.zip -d /var/www/

```

Sorry it took so long (was to a party ^^), but I'm bit rusty when it comes to zip files, but I figured it out. I forgot to tell the unzip what to do (doh) :-/

---


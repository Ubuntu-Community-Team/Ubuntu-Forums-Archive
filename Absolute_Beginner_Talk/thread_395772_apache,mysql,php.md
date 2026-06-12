---
title: "apache,mysql,php"
date: 2007-03-28
forum: Absolute Beginner Talk
---

### Post by pacco on 2007-03-28
I have apache2,php5,and mysql installed no problems.

Except i was wondering how do i enable write access into the /var/www directory without loging in as root
for example i log into ubuntu with my username/password and i use nvu to try and create web pages,but then when i try to save the file into /var/www it denies access.
I have searched these forums before and even googled, any help would be appericiated.

Thank you all in advance

---

### Post by maddog39 on 2007-03-28
In linux you arent allowed to actually login as an admin (aka root) for security sake. However, via the command line you can grant temporary access to root priveleges with a command called sudo. But the easiest way to solve your problem is to add a folder in your home directory called 'public_html' and put all of your files in their. Then to access your website you would use:

[http://localhost/~your_username/](http://localhost/~your_username/)

Where 'your_username' is the username you login to ubuntu with. Hope that helps.

---

### Post by pacco on 2007-03-28
ok thank you very much,i have another quick question

how do i setup my machine so that people on the internet can go to my sites that i have creted to view them,for example i log onto 127.0.0.1 to view my pages i have created,i would like to publish these pages to where everyone can view them,or do i have to sign up for a domain and all that stuff?

Thanks in advance

---

### Post by annda on 2007-03-28
i believe it is safe to let the users belonging to group 'admin' (including you) allow write access to all the files in the directory, while leaving others with read and maybe execute (to change into a subdirectory, i'm not sure how much this is needed on a web file tree). these commands issued in the terminal are useful:
```

sudo chown -R root:admin /var/www
```

and for read+execute rights:
sudo chmod -R 774

or for read rights only:

```
sudo chmod -R 775
```

more info on permissions:
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by DSn0wMan on 2007-03-28
The way I do it is to create a symlink in /var/www to some folder in my home directory (public_html) that contains all my html files. 

After doing that you will have to grant read and execute rights to your apache user on public_html.

---

### Post by annda on 2007-03-28
> **pacco said:**
> how do i setup my machine so that people on the internet can go to my sites that i have creted to view them,for example i log onto 127.0.0.1 to view my pages i have created,i would like to publish these pages to where everyone can view them,or do i have to sign up for a domain and all that stuff?

you can use DynDNS services if you do not have a domain and some hosted space. look here:
[http://www.dyndns.com/services/dns/dyndns/](http://www.dyndns.com/services/dns/dyndns/)

there are also many free servers that can host your files, but the reliable ones place annoying advertising on your website. if that doesn't bother you, google around for free hosting with php and mysql.

---

### Post by pacco on 2007-03-28
ok thank you all for your help

---


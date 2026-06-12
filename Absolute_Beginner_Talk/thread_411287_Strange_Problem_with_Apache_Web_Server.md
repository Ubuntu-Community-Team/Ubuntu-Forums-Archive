---
title: "Strange Problem with Apache Web Server"
date: 2007-04-16
forum: Absolute Beginner Talk
---

### Post by Peter1234123 on 2007-04-16
My website's internal, network only IP is 192.168.1.4, which is static, it worked fine with the Apache default webpage, but when I added my INDEX.HTML and removed the apache one, as I was told to do by the Apache guide I was looking at, I got this error when I accessed the site: 
```
Forbidden
You don't have permission to access /index.html on this server.
Apache/1.3.34 Server at 192.168.1.4 Port 80
```

Then I tried doing: 

```
root@webserver:~# chmod 755 /var/www
```
and still nothing, help please :D

---

### Post by rmemm on 2007-04-16
Check the ownership and permission of the index.html file all the directories above it.  The users/group that runs the apache deamon must have read access to the file and read and probably rx access to all of the containing directories.

I think apache usually runs as www-data.www-data.  Check your setup -- it could be different.

Rob

---

### Post by Peter1234123 on 2007-04-16
OK, I successfully got Apache running on the server, yet for some reason, the theme won't work, as in I only get a white page with text, no images. What's wrong?

---

### Post by Peter1234123 on 2007-04-16
NVM, thanks for the permissions tip, I changed the permissions of each indovidual folder containing artwork to read, now I can view it, thanks!

---


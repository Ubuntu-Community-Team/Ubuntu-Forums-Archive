---
title: "Ubuntu Wine Dreamwear 8 and Xampp"
date: 2007-11-13
forum: Absolute Beginner Talk
---

### Post by amckinn072485 on 2007-11-13
so i have installed Xampp on Ubuntu its running great :guitar: so my problem is this how in the hell do i change the permissions of the folder so i can use dreamweaver to its potential btw dreamweaver runs fine but how do i go about enabling access to the htdocs folder so i can begin working on my sites...

---

### Post by bapoumba on 2007-11-13
Please read my sig, last line.

---

### Post by shad0w_walker on 2007-11-13
Spammer! DON'T RUN THAT COMMAND!

---

### Post by amckinn072485 on 2007-11-13
lol im not so how do i fix this problem without messing up everything

---

### Post by p_quarles on 2007-11-13
You can add your user to group that owns the documents. I'm not sure what that is in XAMPP, but it's likely "www-data." If so, you can add yourself like so:
```
sudo addgroup *username* www-data
```

---

### Post by amckinn072485 on 2007-11-13
tried it no sucess 

[http://i233.photobucket.com/albums/ee213/aqwert12/Denied1.png](http://i233.photobucket.com/albums/ee213/aqwert12/Denied1.png)

---

### Post by p_quarles on 2007-11-13
You'll need to find out who (which user/group) the files actually belong to, then. Try this:
```
ls -l /opt/lampp/htdocs
```

---

### Post by amckinn072485 on 2007-11-13
[PHP]antonio@antonio-laptop:~$ ls -l /opt/lampp/htdocs
total 48
-rw-r--r-- 1 root   root 30894 2007-05-11 05:40 favicon.ico
-rw-r--r-- 1 nobody root   163 2003-10-31 13:15 index.html
d-wx--x--x 2 root   root  4096 2007-11-13 13:53 vallesinc
drwxr-xr-x 2 nobody root  4096 2007-11-13 14:49 webalizer
drwxr-xr-x 6 root   root  4096 2007-11-13 10:26 xampp
antonio@antonio-laptop:~$ 
[/PHP]

its root im assuming....

---

### Post by p_quarles on 2007-11-13
Yeah, but you don't want to add your normal user to the root group. Easier workaround is like so:
```
sudo chown -R *username* /opt/lampp/htdocs
```
That way, you will be the "owner" of those files. If you're running a public server, it's a good idea to create a separate user/group to own htdocs, and then log in as that user when editing it.

---

### Post by amckinn072485 on 2007-11-13
> **p_quarles said:**
> Yeah, but you don't want to add your normal user to the root group. Easier workaround is like so:
```
sudo chown -R *username* /opt/lampp/htdocs
```
That way, you will be the "owner" of those files. If you're running a public server, it's a good idea to create a separate user/group to own htdocs, and then log in as that user when editing it.

thanks that worked i appreciate it ):P

---


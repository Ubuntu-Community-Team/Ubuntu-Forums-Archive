---
title: "Apache2 error / problems"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by ProjectWhat on 2007-04-29
```
ben@Ben-Ubuntu:~$ apache2
apache2: Syntax error on line 189 of /etc/apache2/apache2.conf: Could not open configuration file /etc/apache2/httpd.conf: No such file or directory
ben@Ben-Ubuntu:~$ 
```

I get this error would it help if someone can post thier httpd.conf file here so I can add it over here? Or does anyone know a fix?

---

### Post by annda on 2007-04-29
httpd.conf is kept for backwards compatibility in apache2 and it can be an  empty file. you can easily create one from the terminal:
```

sudo touch /etc/apache2/httpd.conf
```

however, it seems that apache2.conf needs it. can you please find and post line 189 from that file?

UPDATE: sorry, line 189 is standard. it says:

> Include /etc/apache2/httpd.conf

creating an empty file will help.

---

### Post by ProjectWhat on 2007-04-29
I get this error now:
```
ben@Ben-Ubuntu:~$ sudo touch /etc/apache2/httpd.conf
Password:
ben@Ben-Ubuntu:~$ apache2
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
(13)Permission denied: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs
ben@Ben-Ubuntu:~$ 

```

UPDATE:
I just got it to work by this:
sudo apache2

But my index files dont show up, I cant remeber how to fix that. i want index.html,htm,php,etc to show

---

### Post by annda on 2007-04-29
hmm, you can't run a server as user. either add it to services started at boot (recommended: go to system > administration > services, check web server and reboot), or run:

```
sudo apache2
```

---

### Post by annda on 2007-04-29
www files need to be in /var/www

put index.html there.

---

### Post by ProjectWhat on 2007-04-29
> **annda said:**
> www files need to be in /var/www

put index.html there.

Yes yes I know that. I have files there. It list all of my files in the /var/www but it doesnt make my index.html file defualt. So it doesnt show up when i go to localhost. But it is listed with the other files in that directoryy.

---

### Post by annda on 2007-04-29
what do you see in your browser when you go to localhost?

also, if it really is there, and it is called index.html, take a look at the file permissions.

---

### Post by ProjectWhat on 2007-04-29
> **annda said:**
> what do you see in your browser when you go to localhost?

also, if it really is there, and it is called index.html, take a look at the file permissions.


Ok i see what the problem is. .html works but .htm does not. What I see is Virtual listing I think is what its called.

---


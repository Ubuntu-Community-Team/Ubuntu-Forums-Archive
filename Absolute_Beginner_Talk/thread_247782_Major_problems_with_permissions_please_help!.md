---
title: "Major problems with permissions please help!"
date: 2006-08-31
forum: Absolute Beginner Talk
---

### Post by clee on 2006-08-31
hi, I am useing the ubuntu linux lamp server,
when i add uses and put a public_html file in their home dir then when i access it it come up with perimssion deny even when i add a index.html file in it. how do i set it up so that people can view [http://mydomain.com/~clee/](http://mydomain.com/~clee/) other wise i have to set it up manualy all the time on every file?

thanks
Chris

---

### Post by xyz on 2006-08-31
Hi-
This is a good place to go to:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)
Also check the link **psycocats** mentions!  Good luch.

---

### Post by clee on 2006-08-31
I still carnt get it to work :( please help

---

### Post by steve.horsley on 2006-08-31
What user account does the web server process run under? Does that account have access to teh file you want to serve?
You can use **ps -ef** to get a list of running processes.

I don't like the look of that URL. The tilde (~) probably shouldn't be there, but I'm not enough of an Apache expert to know what should be there, or how you arrange different virtual folders.

---

### Post by clee on 2006-08-31
Well i have found out that if you put a public_html in every users home dir then you they can put thier website in there and then it gets hosted. 
so you create a user e.g. bob then add public_html file in his home dir then he can put his website init. then you can access at [http://ip/~bob](http://ip/~bob) on the local network, but i have the problem of the dir being forbiden, so i go in to file zillar (FTP client on windows pc) and change the file attributes to 755 which gives any user to view it over the internet, but i have to do it to every file, do you know how i can get it to automaticly change it for me so i do not have to do it to every file in public_html :(

---

### Post by steve.horsley on 2006-08-31
Hmm. I understand the problem, but I don't have a solution. Parhaps write a scritp that scans the /home directory looking for home directories and runs:
[B]chmod 755 /home/$USER
chmod -R 755 /home/$USER/public_ftp[/B]

something like this (run as root):
#!/bin/bash
```
for USER in $(ls /home); do
    chmod 755 /home/$USER
    chmod -R 755 /home/$USER/public_ftp
done
```

Hey, if that works, it's my first ever bash script. Cool.
put "echo " in front of both chmod's first, to make sure it tries to do the right thing.

---


---
title: "How do i add a user?"
date: 2006-09-14
forum: Absolute Beginner Talk
---

### Post by andy_wood on 2006-09-14
I simply want to a dd a new user and account to ubuntu5.10, but im not sure how to do it. When i go to System -> Administration > Users and Groups....nothing happens. I think this is because I am logged into a user account which is not the admin account (and if this is the case how do i solve this?)

I have tried addclient but a message saying 'Only root may add a user or group to the system'. Is this (again) because I am not logged in as the administrator or it is because i am in the wrong directory in my consolve. I have tried running the command from the root directory....

Thanks

Andy

---

### Post by aysiu on 2006-09-14
If you're not in the admin account (and no one appears to be), try this:
[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

---

### Post by thelocust on 2006-09-14
in terminal put 

sudo adduser (username you want to add)

it will askyou for your root password and then ask some questions for the account and your done.8-)

---

### Post by andy_wood on 2006-09-14
Hey guys. Firstly thank you. I have located the group file. But i dont actaully have the admin line.

instead of admin: x :106:firstuser i have crontab:106. Would it be safe for me to replace the lines in the group file with the lines given in the page that you linked to this thread?

As for the consolde idea....i have tried that but it doesnt prompt me for a password...that's what i find confusing.

Cheers

---

### Post by aysiu on 2006-09-14
So is the only line in your /etc/group file the ```
crontab:106
``` line, or you're just missing the ```
admin:x:106:firstuser
``` line?

It may be easier, if you've already booted into recovery mode to just do this: ```
adduser andy_wood admin
``` than editing the /etc/group file by hand.

---

### Post by andy_wood on 2006-09-14
...just missing the admin line. So when i go into safe mode and see the console, your saying i should just type... adduser andy_wood admin?

---

### Post by aysiu on 2006-09-14
Yes. Give that a shot. If you get an error, record it and post it back here. If you don't get an error, check the /etc/group file and see if it's changed.

---

### Post by andy_wood on 2006-09-14
Ok. I tried that.......

I typed: root@ubuntu:~# adduser andy_wood admin

I got:   The user 'andy_wood' does not exist.

Do i need to do something else?

Thanks again

---

### Post by andy_wood on 2006-09-14
It's ok mate. I sorted it. Thank you very much for your help,. Much appreciated!

Ciao for now

Andy

---


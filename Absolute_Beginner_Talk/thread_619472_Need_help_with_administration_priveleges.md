---
title: "Need help with administration priveleges"
date: 2007-11-21
forum: Absolute Beginner Talk
---

### Post by fettster on 2007-11-21
I need help granting my user privileges to administer the system.  I am using Ubuntu Studio and I selected the install that said it was for manufacturers only, because if I tried to do the regular install, it would crash part way though. Anyways, I was signed on as oem, and I accidentally revoked my privileges to administer the system on my regular user. Then i ran the "prepare for shipping to end user", which deleted the temporary oem user. Now when i log on as my regular user, there is no option under System > Administration, that says "Users and Groups", so I can't edit my privileges and give myself rights to administer the system.  Also, I can't log in as the root user to do this, because when I attempt to log in as root at the main login screen, it says, "The system administrator is not allowed to login from this screen." 

Please help me...

---

### Post by cmnorton on 2007-11-21
If you are logged in as the user who installed the system, then to execute a command

sudo command-you-want-to-execute

You'll be prompted for a password. It's the password you used to login, as long as that user is the user who installed the system. If you want to give another user admin privs, then you'll have to enter the sudo visudo command and enter a user there, using the syntax already in the file as a guide. You're still going to need to know the original installer's username and password to do that.

---

### Post by zvacet on 2007-11-21
Boot in recovery mode and type

```
adduser username admin
```

 username= your username

---

### Post by jaybombalous on 2007-11-21
> **zvacet said:**
> Boot in recovery mode and type

```
adduser username admin
```

 username= your username


agree, just re-add yourself, search the man pages for adduser and read.

---

### Post by bodhi.zazen on 2007-11-21
If that fails boot to recovery mode ... the system will start to command line only, but you will be root.

edit /etc/group

```
nano /etc/group
```

Add your users to the admin group (add your user at the end, comma delimited ie use1,user2)

Ctrl-X to exit, Y to save changes

reboot

You now have sudo access :

[uwiki]RootSudo[/uwiki]

---

### Post by fettster on 2007-11-22
Thank You, 
Now I have administrator priveleges, but I have another problem...
When I try to run System> Administration> Users and Groups it appears at the taskbar saying, "Staring Users and Groups", but after loading for a few seconds, simply disappears and doesn't open.

---


---
title: "Adding users command line!"
date: 2006-07-27
forum: Absolute Beginner Talk
---

### Post by Tadhg on 2006-07-27
Im using ubuntu server without a desktop enviroment and i want to add a few different users and change a few passwords. I was wondering how do i do this in the command line enviroment?

---

### Post by Arisna on 2006-07-27
Use the useradd or adduser commands.

---

### Post by taurus on 2006-07-27
Add a user...

```

sudo useradd -m -G audio,video,games -s /bin/bash john
sudo passwd john

```
Change a password...

```

sudo passwd <userID>

```
For more info,

```

man useradd

```

---

### Post by A2A on 2006-07-27
> Im using ubuntu server without a desktop enviroment and i want to add a few different users and change a few passwords. I was wondering how do i do this in the command line enviroment? 
An alternate would be to install Webmin ([http://www.webmin.com/)]("http://www.webmin.com/%29"), then you would have a GUI based application that you can access from anywhere over the Internet and add/del users, change passwords, and a whole bunch of other cool stuff :p

Regards,

A2A

---


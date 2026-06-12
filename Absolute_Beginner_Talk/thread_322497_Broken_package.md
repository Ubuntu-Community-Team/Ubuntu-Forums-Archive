---
title: "Broken package"
date: 2006-12-20
forum: Absolute Beginner Talk
---

### Post by drito on 2006-12-20
I am trying to fix one broken package and I am getting this:

```
E: /var/cache/apt/archives/mysql-server-5.0_5.0.24a-9_i386.deb: subprocess pre-installation script returned error exit status 1
```

---

### Post by FakeOutdoorsman on 2006-12-20
What are you doing to get this error?  Are you trying to upgrade, install, or remove this package?

---

### Post by drito on 2006-12-20
Everything that, I am afraid. I am getting this error in all cases, and now I can't do anything with Apache, PHP, MySql.

---

### Post by FakeOutdoorsman on 2006-12-20
There might be a problem with a dependency of mysql.

Can you show the output from this command?
```
sudo apt-get check
```

---

### Post by drito on 2006-12-20
> **FakeOutdoorsman said:**
> There might be a problem with a dependency of mysql.

Can you show the output from this command?
```
sudo apt-get check
```

Sorry, I can't. As new in Linux I am not very familiar with this OS. So, I always make mistakes. I tried to remove some more packages and end up with completely ruined Kubuntu.  
Right now I am reinstalling Kubuntu on the other box. Thank you a lot anyway, for trying to help me.

---

### Post by drito on 2006-12-21
This time I used:
 
```
sudo aptitude install apache2 php5-mysql libapache2-mod-php5 mysql-server
``` 

and everything worked just fine. After install I followed instructions from [here]("https://help.ubuntu.com/community/ApacheMySQLPHP?highlight=%28apache%29").

---

### Post by drito on 2006-12-21
...although I can't install phpMyadmin, but who cares, I will learn more using console:)

---


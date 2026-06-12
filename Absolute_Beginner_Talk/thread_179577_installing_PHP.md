---
title: "installing PHP"
date: 2006-05-20
forum: Absolute Beginner Talk
---

### Post by entropy7 on 2006-05-20
Initially when i typed:

sudo apt-cache search php

i got a list of the PHP packages.  Then i went into Synaptic Package Manager and clicked to install Apache. Seems like it installed it, but also seems like it messed something up. Now, i type the above command and i get:


> W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Packages 
(/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) 
- stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Packages 
(/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Packages 
(/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages 
(/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)


sorry to dump this big pile of #@?&% on the thread but this is really frustrating. ](*,) Also, when i type "http://localhost" on the browser, i am used to going into the Apache html document, but it is not doing that.  An alert box says:

> 
The connection was refused when attempting to contact localhost.

thanx for any help you can give a real NOOB getting a LAMP system up and running.

---

### Post by Sef on 2006-05-20
Did you add the repositories?

[https://wiki.ubuntu.com/AddingRepositoriesHowto]("https://wiki.ubuntu.com/AddingRepositoriesHowto")

---

### Post by entropy7 on 2006-05-20
[QUOTE=Sef]Did you add the repositories?

[https://wiki.ubuntu.com/AddingRepositoriesHowto]("https://wiki.ubuntu.com/AddingRepositoriesHowto")[/QUOTE]
I am not sure what that means.  I just did a full install off a CD. It seemed to go OK so I would assume so. Since there is nothing on the system, it is no big deal to just go back and install again.  After all this, i am reluctant to use Synaptic.  Somebody helped me install LAMP before. I could go into the log and see what they typed. It was:

> sudo apt-get install apache php5 mysql-server lib-apache2-mod-auth-mysql  libapache2-mod-php5

Then, i think you had to go into the httpd.conf file and set some options. Hopefully, that will work OK?  Thanx

---

### Post by garner_nc on 2006-05-20
If your connection was refused I bet Apache is not running. I would un-install Apache through Synaptic and then re-install.


    Last week I had a heck of a time getting PHP to work with MySQL. I finally installed PHP from source and got everything working. Read the instructions in the PHP source package. Installing from source is actually pretty easy to do and a good skill to learn.

All the Best,
Doug White

---

### Post by entropy7 on 2006-05-20
the set of errors shown in the intial post i am getting repeatedly such as:

> When i start Synaptic Package Manger 
> when i type:
> sudo apt-get install php5-mysql

What did I do to cause this problem?!?!

---

### Post by adamkane on 2006-05-20
I think you need to update your sources list:
```

sudo apt-get update

``` 
Apache2/PHP4/MySQL4 for breezy (or dapper):
```

sudo apt-get install apache2 php4 mysql-client mysql-server phpmyadmin libapache2-mod-php4 libapache2-mod-auth-mysql php4-mysql

``` 

Apache2/PHP5/MySQL4 for breezy (or dapper):
```

sudo apt-get install apache2 php4 mysql-client mysql-server phpmyadmin libapache2-mod-php4 libapache2-mod-auth-mysql php4-mysql

``` 

Apache2/PHP5/MySQL5 for dapper:
```

sudo apt-get install apache2 php5 mysql-client-5.0 mysql-server-5.0 phpmyadmin libapache2-mod-php5 libapache2-mod-auth-mysql php5-mysql

```

---

### Post by airtonix on 2006-05-22
I can confirm that [adamkane]("http://ubuntuforums.org/member.php?u=76104")'s dapper install suggestion for the lamp scenario works nicley on a dapper setup.

---


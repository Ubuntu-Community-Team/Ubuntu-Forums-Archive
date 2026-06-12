---
title: "how to uninstall the mysql"
date: 2006-08-24
forum: Absolute Beginner Talk
---

### Post by siko on 2006-08-24
i use this to install the mysql 

```
sudo apt-get install apache2 libapache2-mod-security libapache2-mod-php5 php5 mysql-server php5-mysql php5-gd phpmyadmin 
```

but now i want use the mysql 3.23 to develop some codes.i dont konw how to unintall the mysql 5.

now ver is MySQL - 5.0.22-Debian_0ubuntu6.06-log.

thanks.

---

### Post by FuriousLettuce on 2006-08-24
To uninstall mysql, simply do

```
sudo apt-get remove mysql-server
```

However, according to the Ubuntu packages list [http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&version=all&exact=1&keywords=mysql-server]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&version=all&exact=1&keywords=mysql-server"), mysql 3.23 has never been available in Ubuntu. To get it, you will have to find an alternate source or .debs or install from source.

---

### Post by siko on 2006-08-24
yes,i use that command ,but the mysql didnt uninstall.

need reboot ?

---


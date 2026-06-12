---
title: "User who runs apache"
date: 2007-03-12
forum: Absolute Beginner Talk
---

### Post by americaonlan.com on 2007-03-12
How would I go about checking, and if needed, change the user who the apache web server runs under.

I am running dapper drake and apache v2.

Thanks a lot.

---

### Post by bswilson on 2007-03-12
> **americaonlan.com said:**
> How would I go about checking, and if needed, change the user who the apache web server runs under.  I am running dapper drake and apache v2.

The user that runs apache should be **nobody** or **www-data**.  To find out, simply use ps to find out what user is controlling those processes:

```
sudo ps -ef |grep apache
```

To change this in apache2, you must modify the configuration file then restart it.  To do this, first use sudo to edit the file /etc/apache2/conf/httpd.conf and change the user and group to be whatever you wish it to be:

```
sudo cp /etc/apache2/conf/httpd.conf /etc/apache2/conf/httpd.conf.BAK && sudo vi /etc/apache2/conf/httpd.conf
```

While in vi, find the line that says **User www-data** or **User nobody**, and change this to what you want.  Save and exit vi.  Finally, restart apache:

```
sudo /etc/init.d/apache2 restart
```

---

### Post by americaonlan.com on 2007-03-13
bswilson,

Thank you so much. That answered the question that I had wondered about for quite a while. I didn't realize it was based on each application's .conf file (i.e. same format for proftpd.conf, etc.) Thanks so much for the help. It really helped me out.

---


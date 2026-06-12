---
title: "Apache ~"
date: 2006-05-07
forum: Absolute Beginner Talk
---

### Post by GaFFy on 2006-05-07
I have Apache PHP MySQL installed and everthing works great...
Well almost everything, if i go to just localhost with no page name then it comes up with the download file dialog and the filename is ~

Anyone know why and how to fix this, it should open index.php :confused:

---

### Post by moberry on 2006-05-07
When you goto localhost/index.php does that load up the right file? If so edit your apache config file.. i forget the exact string in the file. but look for a section that has "index.htm index.html" etc. those are the files the server looks for when it loads up a page by directory.

---

### Post by GaFFy on 2006-05-07
yes index.php works correctly if you go directly to it.
I checked the conf and the DirectoryIndex does have index.php listed

---

### Post by moberry on 2006-05-07
hmm, I had this problem too, cannot remember how i fixed it.

---

### Post by GaFFy on 2006-05-08
Anyone else know how to fix it?

---

### Post by stefan_tech on 2006-06-04
...bump

I have the same problem here.  Any help would be greatly appreciated!

---

### Post by mani_kapyaw on 2006-06-04
I'm very new Linux and trying to find help how to install apache, but im kinda experienced under windows. 

I think the problem here is setting the default pages, i forgot what to call this page, but if you try to put an index.html there it will load index.html without indicating the file, so its just a matter of editing the config file for your apache and making index.php one of your default pages.

I'm not very sure though as i said im very new to linux, but if apache under linux and windows works the same then this is the only problem i see.

---

### Post by adamkane on 2006-06-07
Install this way:

Apache2/PHP4/MySQL4 (breezy or dapper):
```

sudo apt-get install apache2 php4 mysql-client mysql-server phpmyadmin libapache2-mod-php4 libapache2-mod-auth-mysql php4-mysql

```

Apache2/PHP5/MySQL4 (breezy or dapper):
```

sudo apt-get install apache2 php5 mysql-client mysql-server phpmyadmin libapache2-mod-php5 libapache2-mod-auth-mysql php5-mysql

```

Apache2/PHP5/MySQL5 (dapper):
```

sudo apt-get install apache2 php5 mysql-client-5.0 mysql-server-5.0 phpmyadmin libapache2-mod-php5 libapache2-mod-auth-mysql php5-mysql

```

Reboot (or start mysql manually).

Open phpmyadmin:
[http://localhost/phpmyadmin](http://localhost/phpmyadmin)

Name: root
Pass: [blank]

---


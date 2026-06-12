---
title: "[SOLVED] need my apache2 dir back"
date: 2007-12-07
forum: Absolute Beginner Talk
---

### Post by jtann on 2007-12-07
i uninstalled apache2 then delleted my apach2 dir. then did apt get install apache but does not put back dir.

---

### Post by llamakc on 2007-12-07
Which directory are you speaking of? The DocumentRoot? Or what?

---

### Post by jtann on 2007-12-07
/etc/apache2/

---

### Post by taurus on 2007-12-07
Can you just create it by hand?

```
sudo mkdir /etc/apache2
```

---

### Post by jtann on 2007-12-07
i did that but install put nothing into the dir

---

### Post by ruibernardo on 2007-12-07
Try reinstalling the package apache2.2-common. That's the package that have the apache configuration files. 

The fact that you deleted the /etc/apache2 directory might be a problem because it is needed to purge the apache2.2-common package to reinstall it after.

---

### Post by jtann on 2007-12-07
i did this got all my dir's back but no config file

---

### Post by ruibernardo on 2007-12-08
It happened because you deleted the directory. To APT the files should be there, so it didn't restore them. A workaround to restore the original conf files could be the following:[INDENT]- Download the apache2.2-common deb package (this one is for Gutsy):
```
wget -c [http://archive.ubuntu.com/ubuntu/pool/main/a/apache2/apache2.2-common_2.2.4-3build1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/a/apache2/apache2.2-common_2.2.4-3build1_i386.deb)

```- Extract it with dpkg -x to a directory:
```
dpkg -x apache2.2-common_2.2.4-3build1_i386.deb temp_dir
```- Copy the files you want from the extracted directory to /etc/apache2/:
```
cd temp_dir/etc/apache2
sudo cp apache2.conf /etc/apache2

```[/INDENT]Didn't tested it, but should work. Don't know if the links between sites-available and sites-available are restored. Maybe you need to link them by hand and purge the package, then reinstall again so all is installed again and links restored by dpkg (I'm guessing here).

---


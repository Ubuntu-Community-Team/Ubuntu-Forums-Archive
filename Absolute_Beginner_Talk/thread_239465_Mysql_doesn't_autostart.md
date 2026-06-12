---
title: "Mysql doesn't autostart"
date: 2006-08-19
forum: Absolute Beginner Talk
---

### Post by MatsB on 2006-08-19
I've folloed this guide to install Mysql but can't get it to autostart:

cd /install
tar -zxvf mysql*
cd mysql*
./configure --prefix=/usr/local/mysql
make
make install
groupadd mysql
useradd -g mysql mysql
scripts/mysql_install_db
chown -R root /usr/local/mysql
chown -R mysql /usr/local/mysql/var
chgrp -R mysql /usr/local/mysql
rm -f /etc/my.cnf
cp support-files/my-medium.cnf /etc/my.cnf
echo /usr/local/mysql/lib/mysql >> /etc/ld.so.conf
echo /usr/local/lib >> /etc/ld.so.conf
ldconfig –v
cp support-files/mysql.server /etc/init.d/mysql
/usr/local/mysql/bin/mysqld_safe --user=mysql &

cd /etc/rc3.d/
ln -s ../init.d/mysql S85mysql
ln -s ../init.d/mysql K85mysql
cd /etc/rc5.d/
ln -s ../init.d/mysql S85mysql
ln -s ../init.d/mysql K85mysql
cd /etc/init.d/
chmod 755 mysql

Running this from CLI works just fine: /usr/local/mysql/bin/mysqld_safe --user=mysql &
I'm running on Ubuntu LTS 6.06

---

### Post by statue on 2006-08-19
Might want to remmeber to use "apt-get install" or "aptitude install"from now on....much less hassle as they install rather painlessly...other than that im no help for ya, sorry

---

### Post by MatsB on 2006-08-19
> **statue said:**
> Might want to remmeber to use "apt-get install" or "aptitude install"from now on....much less hassle as they install rather painlessly...other than that im no help for ya, sorry

I know but I want to install a certain version of Mysql that's why I'm doing it the "hard way"

---


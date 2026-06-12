---
title: "vsftpd"
date: 2007-10-28
forum: Absolute Beginner Talk
---

### Post by johnnyw on 2007-10-28
is there any front end GUI that allows me to properly config vsftpd??

just taken away the anon accounts and so on but I need further configuration and dont know where to gather more info

[https://help.ubuntu.com/6.06/ubuntu/serverguide/C/ftp-server.html](https://help.ubuntu.com/6.06/ubuntu/serverguide/C/ftp-server.html)


this is my source

TIA

J

---

### Post by johnnyw on 2007-10-28
would someone help me please??

thx

---

### Post by jtann on 2007-10-28
[http://www.webmin.com/third.html](http://www.webmin.com/third.html).
if your using webmin. just search for vsftpd on this page.

---

### Post by joop905 on 2007-10-28
in terminal:

sudo apt-get install build-essential pkg-config \

libsqlite3-dev libsexy-dev \
libgtkspell-dev libgtkhtml3.8-dev \
libglib2.0-dev libdbus-glib-1-dev \
libcurl3-dev libpcre3-dev \
libxslt1-dev libnotify-dev libtool \
automake1.9 autoconf firefox-dev

cd /tmp

wget [http://ftd4linux.nl/releases/openftd-1.0.1.tar.bz2](http://ftd4linux.nl/releases/openftd-1.0.1.tar.bz2)

tar -xvjf openftd-1.0.1.tar.bz2

cd openftd-1.0.1

./configure

make

---

### Post by johnnyw on 2007-10-28
could u explain what this does?

---


---
title: "how to install webmin ?"
date: 2007-11-22
forum: Absolute Beginner Talk
---

### Post by Willye on 2007-11-22
hi my friends i have this package: webmin_1.380_all.deb how i must to install it ?

---

### Post by Paul820 on 2007-11-22
Just double click the package and the system will do the rest.

---

### Post by Dr Small on 2007-11-22
From the terminal:
```
sudo dpkg -i webmin_1.380_all.deb
```

Then to access Webmin, In your browser, go to :
[https://localhost:10000](https://localhost:10000)

If you setup Usermin from Webmin, the address will be:
[https://localhost:20000](https://localhost:20000)

Good Luck!

Dr Small

---

### Post by Willye on 2007-11-22
ok thanks, i had to do this:
apt-get install perl libnet-ssleay-perl openssl libauthen-pam-perl libpam-runtime libio-pty-perl libmd5-perl
because i had problems with dependences

---


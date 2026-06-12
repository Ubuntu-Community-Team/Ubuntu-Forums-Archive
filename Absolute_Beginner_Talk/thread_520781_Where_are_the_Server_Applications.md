---
title: "Where are the Server Applications"
date: 2007-08-08
forum: Absolute Beginner Talk
---

### Post by CadmannUK on 2007-08-08
Hi,
I installed the Server 7.04 version with the LAMP option, but because there is no GUI with that I sudo app-install ubuntu-desktop onto the PC runing Ubuntu.

No I have a nice server that comes up with a text window. I startx and get the Ubuntu desktop, but none of the server apps are there, (or not on the menus anyway).

How do I get a graphical front end to stuff like Apache or the other web stuff. I am really new to all this, so please bear with me.

Thanks anyway.

Cad

---

### Post by FakeOutdoorsman on 2007-08-08
There is no GUI for Apache, but mySQL has phpmyadmin.  I would recommend reading this first:
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

If your server is just for local development (not public), then XAMMP might be easier for you:
[HOWTO: Setup easy web development environment (XAMPP)]("http://ubuntuforums.org/showthread.php?t=223410")
Do not use XAMPP as a public server.

---

### Post by M374llic4 on 2007-08-08
> **FakeOutdoorsman said:**
> There is no GUI for Apache, but mySQL has phpmyadmin.  I would recommend reading this first:
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

If your server is just for local development (not public), then XAMMP might be easier for you:
[HOWTO: Setup easy web development environment (XAMPP)]("http://ubuntuforums.org/showthread.php?t=223410")
Do not use XAMPP as a public server.

If i may ask, whats wrong with Xampp for public? What should be used instead?

---

### Post by FakeOutdoorsman on 2007-08-08
XAMPP is designed to be a easier to install and use as a local development server and not so much a public web server.
[URL="http://www.apachefriends.org/en/xampp-linux.html#381"]
A matter of security[/URL] (from apachefriends.org - the XAMPP site):
1. The MySQL administrator (root) has no password.
2. The MySQL daemon is accessible via network.
3. ProFTPD uses the password "lampp" for user "nobody".
4. PhpMyAdmin is accessible via network.
5. Examples are accessible via network.
6. MySQL and Apache running under the same user (nobody).

If you want a secure public server, follow the instructions here:
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by M374llic4 on 2007-08-08
> **FakeOutdoorsman said:**
> XAMPP is designed to be a easier to install and use as a local development server and not so much a public web server.
[URL="http://www.apachefriends.org/en/xampp-linux.html#381"]
A matter of security[/URL] (from apachefriends.org - the XAMPP site):
1. The MySQL administrator (root) has no password.
2. The MySQL daemon is accessible via network.
3. ProFTPD uses the password "lampp" for user "nobody".
4. PhpMyAdmin is accessible via network.
5. Examples are accessible via network.
6. MySQL and Apache running under the same user (nobody).

If you want a secure public server, follow the instructions here:
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

Yes, but if you run "/opt/lampp/lampp security" it goes through a whole setup to add passwords and change the default logins, then you go to the security portion of the xampp main page to check security. it will tell you if it is secure or not. Once all passwords are added, its as secure as any other flavor of lampp, just easier.

It just comes unsecured for testing, once you run security, your good to go.

---

### Post by willskills on 2007-08-08
> **M374llic4 said:**
> Yes, but if you run "/opt/lampp/lampp security" it goes through a whole setup to add passwords and change the default logins, then you go to the security portion of the xampp main page to check security. it will tell you if it is secure or not. Once all passwords are added, its as secure as any other flavor of lampp, just easier.

It just comes unsecured for testing, once you run security, your good to go.

True that - I use it internally at work, but obviously still needs to be secure to some degree - love XAMPP.

---

### Post by FakeOutdoorsman on 2007-08-08
> **M374llic4 said:**
> Yes, but if you run "/opt/lampp/lampp security" it goes through a whole setup to add passwords and change the default logins, then you go to the security portion of the xampp main page to check security. it will tell you if it is secure or not. Once all passwords are added, its as secure as any other flavor of lampp, just easier.

It just comes unsecured for testing, once you run security, your good to go.

Does XAMPP install go through "/opt/lampp/lampp security" by default?  I'm unsure if it does or not.  Otherwise I can see a lot of people missing that step.

---

### Post by M374llic4 on 2007-08-10
> **FakeOutdoorsman said:**
> Does XAMPP install go through "/opt/lampp/lampp security" by default?  I'm unsure if it does or not.  Otherwise I can see a lot of people missing that step.

No, it does not, but after the install and in the install manual it says you should run it.

---


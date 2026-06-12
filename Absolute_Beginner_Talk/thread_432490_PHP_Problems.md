---
title: "PHP Problems"
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by offramp13 on 2007-05-04
I have followed a [guide]("http://www.howtoforge.com/perfect_setup_ubuntu_6.10") to install LAMP. But, when I go to localhost and try to run a php script it just shows the source code. Thanks for your help.

---

### Post by darkrose on 2007-05-04
You might just need to enable the php module, open a terminal and run:
sudo a2enmod php
or
sudo a2enmod php5

---

### Post by indytim on 2007-05-04
You are trying to "run" it via a legitmate address like:

[PHP]http://localhost/index.php[/PHP]

Sorry to be so basic, but I've seen some incredible "different" ways of attempting to run php scripts in the past:) .

IndyTim

---

### Post by mendingo84 on 2007-05-04
have you installed the package: php5?

---


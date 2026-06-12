---
title: "MySQL Auto Start"
date: 2008-03-27
forum: Absolute Beginner Talk
---

### Post by commondork on 2008-03-27
I have to manually start my MySQL server each time (sudo /etc/init.d/mysql start).  How can I make the MySQL server automatically start when I boot my system?

---

### Post by opscure on 2008-03-27
Applications->Settings->Auto Started Applications
click new
enter name, description and command
sudo /etc/init.d/mysql start

---


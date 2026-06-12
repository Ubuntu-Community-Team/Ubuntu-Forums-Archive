---
title: "Membership Management/Church Management"
date: 2006-07-23
forum: Absolute Beginner Talk
---

### Post by kpurcell on 2006-07-23
I was wondering if anyone here in a church or religious organization is using Linux in their office and has a membership tracking program for Linux.  It would have to track name, address, etc.  Attendance, financial contributions, and what groups within the organization they are a part of.

Is there anything that is Linux based that does this?

---

### Post by ubuntu-geek on 2006-07-23
Web based: [http://www.flamingspork.com/projects/memberdb/](http://www.flamingspork.com/projects/memberdb/)
Web based: [http://membership-software.org/](http://membership-software.org/)
Web based: [http://www.infocentral.org/](http://www.infocentral.org/)

I hope that can get you pointed in the right direction. I am not sure of any membership tracking programs that run directly in gnome/kde but you could setup a local webserver/database and run the above program on the local machine.

---

### Post by kpurcell on 2006-07-24
Thanks ubuntu-geek, that is a big help.  The InfoCentral one looks promising.  Have you ever installed anything like this?

---

### Post by ubuntu-geek on 2006-07-24
Not these programs directly but I have installed lots of php/mysql applications over the years. If you need help getting it installed on your local computer I can help.

---

### Post by kpurcell on 2006-07-24
> **ubuntu-geek said:**
> Not these programs directly but I have installed lots of php/mysql applications over the years. If you need help getting it installed on your local computer I can help.

That would be great.  I downloaded Infocentral and the instructions are pretty cryptic.  It told me to isntall a list of programs including apache, php4 and others.

From the readme.txt
```
For Debian GNU/Linux users, you should install these packages:
mysql-server, mysql-common, mysql-client, php4, php4-mysql, php4-gd2,
php4-pear, and whatever Apache packages suit your needs.
```

I did that.

Next it says,```

PHP   - Version 4.1 or greater
      - GD enabled
      - PEAR enabled
      - gettext enabled
      - register_globals turned OFF (see below)
MySQL - Version 4.0 or greater
```

Hmm.  No clue here.

---


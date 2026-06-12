---
title: "Proftpd"
date: 2006-09-01
forum: Absolute Beginner Talk
---

### Post by dgcarter on 2006-09-01
When I do apt-get install proftpd

It says that it can't find the package
I also can't find the package in Synaptic

So how do I get Proftpd?

---

### Post by KingBahamut on 2006-09-01
[http://doc.gwos.org/index.php/FTP_Server](http://doc.gwos.org/index.php/FTP_Server)

Try that.

---

### Post by professor_chaos on 2006-09-01
proftp is in the universe repository.

check out this link to see how to add.
[https://help.ubuntu.com/ubuntu/desktopguide/C/extra-repositories.html](https://help.ubuntu.com/ubuntu/desktopguide/C/extra-repositories.html)

---

### Post by ape on 2006-09-01
You need to add the universe repository to your /etc/apt/sources.list.

right now you probably have something like:

[FONT="Courier New"]deb [http://ubuntu.cs.utah.edu/ubuntu](http://ubuntu.cs.utah.edu/ubuntu) dapper main restricted[/FONT]

Just add universe to the end of it like this:

[FONT="Courier New"]deb [http://ubuntu.cs.utah.edu/ubuntu](http://ubuntu.cs.utah.edu/ubuntu) dapper main restricted universe[/FONT]

---


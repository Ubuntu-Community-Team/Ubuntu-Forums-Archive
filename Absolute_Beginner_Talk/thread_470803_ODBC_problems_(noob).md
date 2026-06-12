---
title: "ODBC problems (noob)"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by SloS13 on 2007-06-11
Im a noob to Ubuntu and linux in general, running Feisty.

How do I set up an ODBC connection?  I've used the package manager to download and install iodbc but it didnt create a menu item, nor does anything show up for iodbc when I do a search in the filesystem.  Did I miss a step?



**Installed the following packages:**
iodbc (3.52.4-5)
libglib1.2 (1.2.10-17build1)
libgtk1.2 (1.2.10-18)
libgtk1.2-common (1.2.10-18)
libiodbc2 (3.52.4-5)

---

### Post by thelinuxguy on 2007-06-11
This gets a GUI running:
```

iodbcadm-gtk

```

But it turns out that you need to install an ODBC driver for the specific database you want to connect to.
For MySQL, you will need to download the appropriate drivers from [http://mysql.org/downloads/connector/odbc/3.51.html](http://mysql.org/downloads/connector/odbc/3.51.html).
Installation steps can be found at [http://dev.mysql.com/doc/refman/5.0/en/myodbc-connector.html](http://dev.mysql.com/doc/refman/5.0/en/myodbc-connector.html)
You will also need to install libltdl3
```

sudo apt-get install libltdl3

```

I tried the above but apparently made some mistake and ended up with error messages like
```

1: SQLDriverConnect = [iODBC][Driver Manager]/usr/local/lib/libmyodbc3.so: undefined symbol: SQLWritePrivateProfileString (0) SQLSTATE=00000
2: SQLDriverConnect = [iODBC][Driver Manager]Specified driver could not be loaded (0) SQLSTATE=IM003

```

Your result could be more encouraging. Let me know.

Take a look here as well: [http://www.flatmtn.com/computer/Linux-mySQL.html](http://www.flatmtn.com/computer/Linux-mySQL.html)

---


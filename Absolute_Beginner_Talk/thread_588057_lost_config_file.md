---
title: "lost config file"
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by phoenix24x on 2007-10-23
i  lost a config file for a package. i tried purging the package and re-installing it but that didnt put the file back. is there a way to get it back?

name of the file is krb5.conf

---

### Post by phoenix24x on 2007-10-23
anyone??

---

### Post by kellemes on 2007-10-23
have you tried searching? maybe there are copies somewhere..
```
sudo updatedb
sudo locate krb5.conf
```

---

### Post by phoenix24x on 2007-10-23
yea...but its an edited version, i was hoping to get the original file back.

---

### Post by be4truth on 2007-10-23
Go to the directory where the file is and rename your edited file

```
mv krb5.conf krb5.conf.mybackup
```

Then you reinstall the package. You should get the original conf. file.

---


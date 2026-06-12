---
title: "Installing packages apt-setup command not found"
date: 2006-07-04
forum: Absolute Beginner Talk
---

### Post by cptvitamin on 2006-07-04
OK, total nube here.  Installed Ubuntu just fine.  Now I want to start installing packages and none with apt-get and none are found.  I assume I have to use apt-setup to tell apt where to look for packages.  However apt-setup is not installed with Ubuntu dapper drake?!?!  When I try to run it I get command not found. 

Any ideas?

---

### Post by Jagot on 2006-07-04
To install something:

```
sudo apt-get install [name of package]
```

Or, even better:

```
sudo aptitude install [name of package]
```

Take a look at this tutorial:

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---


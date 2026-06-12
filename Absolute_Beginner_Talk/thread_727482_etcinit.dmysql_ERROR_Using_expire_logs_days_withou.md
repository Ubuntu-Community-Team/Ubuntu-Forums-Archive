---
title: "* /etc/init.d/mysql: ERROR: Using expire_logs_days without log_bin crashes the serve"
date: 2008-03-17
forum: Absolute Beginner Talk
---

### Post by drndrw on 2008-03-17
```
 * /etc/init.d/mysql: ERROR: Using expire_logs_days without log_bin crashes the server. See README.Debian.gz

```

Hey guys. My mysql server is not starting up now. I just installed some header files for ISPConfig, and I made some changes to the config file, but it doesn't turn back on. Why is this? What can it do?

---

### Post by spiderbatdad on 2008-03-17
Maybe multiple instances are being called? Google the error and see what turns up.

---

### Post by drndrw on 2008-03-17
Okay, well I modified my.cnf. I reinstalled mysql-server. Same error. What do I need to uninstall and then reinstall?

---

### Post by spiderbatdad on 2008-03-17
This is the guide that got me started: [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by drndrw on 2008-03-17
I uninstalled all of those packages and reinstalled them. It still doesn't work.

---

### Post by apfejes on 2008-04-20
I doubt you're still having this problem, but it turned up for me under an upgrade of hardy heron.

It seems that my /etc/myqsl/my.conf file was using the parameter expire_logs_days, which requires the log_bin parameter be turned on.  Sure enough, I opened the file and log_bin was commented out.  By turning it on (e.g, removing the '#' character infront of it), everyone was happy again.

hope that helps someone in the future.

---

### Post by 316097 on 2008-04-26
> **apfejes said:**
> I doubt you're still having this problem, but it turned up for me under an upgrade of hardy heron.

It seems that my /etc/myqsl/my.conf file was using the parameter expire_logs_days, which requires the log_bin parameter be turned on.  Sure enough, I opened the file and log_bin was commented out.  By turning it on (e.g, removing the '#' character infront of it), everyone was happy again.

hope that helps someone in the future.

This helped me, thanks alot, I also got this after upgrade to Hardy.

---

### Post by thunderbirdje on 2008-07-18
Helped me too after installing partial packages from Hardy repos.

But in my case the file called my.cnf (instead of my.conf). 

Thanks a lot!

---


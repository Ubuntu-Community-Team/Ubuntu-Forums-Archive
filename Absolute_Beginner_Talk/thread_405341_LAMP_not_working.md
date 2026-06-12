---
title: "LAMP not working"
date: 2007-04-09
forum: Absolute Beginner Talk
---

### Post by mystically on 2007-04-09
I followed this [http://www.supriyadisw.net/2006/12/lamp-installation-on-ubuntu](http://www.supriyadisw.net/2006/12/lamp-installation-on-ubuntu)

first time I tried it it works but I uninstalled php5 and replaced with php4 then after I tried to install php5 back on the page phpinfo it didn't show up and theres a download  that's phtml. Can anyone help me?

---

### Post by mssever on 2007-04-10
Your post is a little difficult to understand, but it sounds like maybe PHP isn't getting called by Apache for some reason. Look in /etc/apache2/mods-enabled and make sure there's a php5.conf and a php5.load in the directory (I'm not sure if they're php5 or just php; my system is so customized...). If not, that's your problem.

Otherwise, look in /var/log/apache for error messages.

If all else fails, backup your settings, then purge and reinstall.

---

### Post by mystically on 2007-04-10
I already reinstalled apache and php all together as pointed above. when I point to a php page it just makes me download a phtml file like anyother download files.

First time I installed all it works but after I switched to php4 and tried to switch back to php5 it didn't work.

php5.conf is not here

EDIT it works now. I moved the php5.conf and php5.load from the mod-avanble directory to the mod-enable dir

---

### Post by mssever on 2007-04-10
Have you tried the other things I suggested? If so, what were the results? In addition to my previous suggestions, you can also try using mod_info to find out if PHP is properly installed:
```
sudo a2enmod info
```
Configure mod_info according to the instructions in the Apache manual: [http://httpd.apache.org/docs/2.0/mod/mod_info.html](http://httpd.apache.org/docs/2.0/mod/mod_info.html)

Restart Apache:
```
sudo apache2ctl graceful
```


Navigate to the url you configured and see if PHP is listed.

---

### Post by mssever on 2007-04-10
Just caught your edit. Glad it's working.

---

### Post by mystically on 2007-04-10
Ya just moved directories.

---


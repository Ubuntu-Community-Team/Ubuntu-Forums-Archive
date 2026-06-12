---
title: "Inadvertanly delete root from MySql"
date: 2007-01-30
forum: Absolute Beginner Talk
---

### Post by peejaygee on 2007-01-30
Dear All, 

I was using phpMyAdmin, and haven't used it for a while, checked the root (localhost) button, and clicked [Go] thinking it was going to go into the privileges page, as I clicked [Go] I got that 'Doh' feeling, as I realised I was dropping a user, now I can't get back in?

I've tried a few examples on the web to help me out, like running msql in safe mode, but this doesn't allow me to re-add the user, I've tried doing it through another command prompt (I'm using a SSH) but I can't get it to work.

I would really like to uninstall mysql totally and re-install it, as I've got no major databases in there, as it is a fresh-mess around install, but I really don't want to do that formidable re-install?

Can anybody give me any tips or points to re-enable the root account for localhost within mysql? either from command prompt, or using phpMyAdmin?

Thanks in Advance.

Paul.

---

### Post by phossal on 2007-01-31
Reinstall. ;) 

It's not formidable. Just remove the packages *completely*, and then install them in a simple command:
```
sudo apt-get install mysql-server mysql-client
```

Or... 

Check out the [documentation.]("http://dev.mysql.com/doc/refman/5.0/en/resetting-permissions.html")

---


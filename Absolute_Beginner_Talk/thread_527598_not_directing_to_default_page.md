---
title: "not directing to default page"
date: 2007-08-16
forum: Absolute Beginner Talk
---

### Post by jakebur01 on 2007-08-16
when i access my var/www/ directory via [http://myhost.dyndns.org](http://myhost.dyndns.org)  all I get is a page with everything listed in the directory.

I would like index.php to be the default page. How do I make this happen?

---

### Post by jamvegan on 2007-08-17
If you are running Apache, you need to add index.php to the DirectoryIndex line of your configuration.  In Apache 2, as installed by apt, this is in the file /etc/apache2/mods-enabled/dir.conf.  [Apache Documentation]("http://httpd.apache.org/docs/2.2/mod/mod_dir.html#directoryindex")

---


---
title: "PHPMyAdmin"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by ecochran on 2007-05-31
I have been trying to find best practices on securing PHPMyAdmin but haven't found anything that has been very helpful.  Everything points to htaccess files and the PHPMyAdmin authentication.  What I am looking for is a way to secure it from external access.  Can I place it on a different port other than the standard 80 so that I can block access through my firewall?  How would I do this?

Thanks,
Ethan

---

### Post by Cypher on 2007-05-31
As you've found out phpMyAdmin doesn't employ any security of it's own. So most usually go thr HTACCESS/HTPASSWD route. Most web-hosts usually put phpMyAdmin within the realm of CPanel's control and since you have to authenticate to CPanel, phpMyAdmin is safe.

If you wanted to put phpMyAdmin on a seperate port, this is a Apache configuration change. You can create VirtualHost on a port known only to you that will run phpMyAdmin and that you can block in your firewall.

Check out this documentation on [VirtualHost]("http://httpd.apache.org/docs/2.0/vhosts/examples.html").

---


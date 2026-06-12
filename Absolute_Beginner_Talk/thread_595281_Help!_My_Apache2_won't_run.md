---
title: "Help! My Apache2 won't run"
date: 2007-10-28
forum: Absolute Beginner Talk
---

### Post by jmnemonic on 2007-10-28
Here's the error message...

I've found an error message....

* Starting apache 2.0 web server...
Syntax error on line 9 of /var/www/vhosts/birches.org/conf/vhost.conf:
<VirtualHost> cannot occur within <VirtualHost> section
   ...fail!


Here are the first nine lines of the file....

# ATTENTION!
# DO NOT MODIFY THIS FILE OR ANY PART OF IT. THIS CAN RESULT IN IMPROPER PLESK
# FUNCTIONING OR FAILURE, CAUSE DAMAGE AND LOSS OF DATA. IF YOU REQUIRE CUSTOM
# MODIFICATIONS TO BE APPLIED TO THE CONFIGURATION, PLEASE, PERFORM THEM IN THE
# FOLLOWING FILE(S):
# /var/www/vhosts/birches.org/conf/vhost.conf
# /var/www/vhosts/birches.org/subdomains/<subdomain-name>/conf/vhost.conf

<VirtualHost 212.241.214.65:80>

I'm going mad trying to understand what the problem is, can anyone help?

---

### Post by Cato2 on 2007-10-28
Assuming you have several <VirtualHost> directives, make sure you are closing off the previous <VirtualHost> section, using a </VirtualHost> directive, before you start the next one.  

See [http://www.unix-girl.com/geeknotes/apache_virtual_host_conf.html](http://www.unix-girl.com/geeknotes/apache_virtual_host_conf.html) for a fairly long example and note the closing directive at end.

---


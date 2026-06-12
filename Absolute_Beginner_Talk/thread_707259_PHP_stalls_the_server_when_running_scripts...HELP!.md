---
title: "PHP stalls the server when running scripts...HELP!"
date: 2008-02-25
forum: Absolute Beginner Talk
---

### Post by djsky on 2008-02-25
I have Gutsy distro installed with Apache2, PHP5 and mySQL servers. I created a test.php file to make sure php scripts are executing properly and it worked just fine. However, every time I try to run a regular PHP script, the server stalls. In firefox, when I run a PHP script, it gets stuck on "waiting for www.myserver.com" and doesn't go anywhere else. After that, any requests to other pages on the server get stuck on the same message.  

I noticed that this happens primarily during user registration.  I'm trying to play around with different auction php scripts but every time any of them gets to user registration, it stalls.  If I stop the operation in the browser and let it sit for about 15 minutes, the server comes back.  Sometimes, I can't even restart Apache again.

I reinstalled Apache2 and PHP5 probably twice already to try to resolve this to no avail.

PHP5 is installed with the following mods enabled:

core mod_log_config mod_logio prefork http_core mod_so mod_alias mod_auth_basic mod_authn_file mod_authz_default mod_authz_groupfile mod_authz_host mod_authz_user mod_autoindex mod_cgi mod_dir mod_env mod_include mod_mime mod_negotiation mod_php5 mod_rewrite mod_setenvif mod_ssl mod_status mod_suexec



Please help!!!

---

### Post by jonabyte on 2008-02-25
You may want to check the actual php script and debug it, it sounds like there is a problem with the coding.
I know when I run bad scripts it does basically the same thing.

---

### Post by djsky on 2008-02-25
> **jonabyte said:**
> You may want to check the actual php script and debug it, it sounds like there is a problem with the coding.
I know when I run bad scripts it does basically the same thing.

I tried 3 different auction scripts and they all do the same thing.  Could it possibly be the server php configuration itself?  What should I look for?

---

### Post by djsky on 2008-03-05
I tried a few more scripts and they all do the same thing:  stall the server when submitting registration.

I just find it hard to believe that it could be the scripts themselves.  I think somewhere in the PHP setting something is not right.  


Can someone please point me in the right direction on what I can try to fix???  Please???

---


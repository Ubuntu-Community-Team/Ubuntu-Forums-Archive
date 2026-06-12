---
title: "[SOLVED] Blank PHP page in Apache2, after reinstalling"
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by lobo-tuerto on 2008-01-16
Hello guys,

I was playing around with an instalation of Apache2, after a while it became unstable and I uninstalled it. Even deleted the /etc/apache2 folder.

But after removing it, I tried to uninstall Apache2, and I was getting error messages about apache2.conf not existing in the /etc/apache2 folder... and indeed, it was missing, along with other files. Anyone here knows the reason why it didn't reinstall "complete" like the first time?

Well I was able to reinstall Apache2 completely using the Synaptic package manager.

Now I have another problem: Before installing PHP5, I would click over a php page, and the browser would try to send it to me. After installing it, it would no longer try to send it to me... it would only display a BLANK page, nothing in it, no error logs aswell. Anyone knows what's going on? (I already searched the forums, but couldn't find anything related to my problem).

Help pls :(

---

### Post by bullgr on 2008-01-16
it seems that you mess your installation.
i believe that none can help you exactly with this.

go there [http://doc.ubuntu.com/ubuntu/serverguide/C/](http://doc.ubuntu.com/ubuntu/serverguide/C/)
and see step by step how you can install-configure apache
and maybe you can find a solution.

sorry...

---

### Post by lobo-tuerto on 2008-01-16
Hmmm I don't think I have messed it up bad, since I read in the guide that you could remove that folder and nothing wrong would happen. I think that messing around with apache shouldn't mean you have to format your drive and reinstall Ubuntu fresh, just to get it up and running, do you?

I used this line to remove everything:
sudo apt-get remove --purge apache2 apache2-mpm-prefork apache2-utils apache2.2-common libapache2-mod-php5 libapr1 libaprutil1 libdbd-mysql-perl libdbi-perl libmysqlclient15off libnet-daemon-perl libplrpc-perl libpq5 mysql-client-5.0 mysql-common mysql-server mysql-server-5.0 php5-common php5-mysql

Then I reinstalled following step by step this guide:
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

Everything installed ok, not errors, but still I'm getting the blank php pages.
Maybe I need to add these lines:
AddType application/x-httpd-php .php .phtml
AddType application/x-httpd-php-source .phps

But I don't know where :(

---

### Post by hyper_ch on 2008-01-16
A friend of mine had a similar problem a while ago. The installation of apache did not create any config files... we couldn't work out why that happened.

Post the output of:

```

ls -alR /etc/apache2

```

---

### Post by lobo-tuerto on 2008-01-16
```
/etc/apache2/:
total 60
drwxr-xr-x   7 root root  4096 2008-01-16 02:59 .
drwxr-xr-x 126 root root 12288 2008-01-16 02:41 ..
-rw-r--r--   1 root root 10384 2008-01-16 02:59 apache2.conf
drwxr-xr-x   2 root root  4096 2008-01-16 02:36 conf.d
-rw-r--r--   1 root root   895 2007-10-04 17:42 envvars
-rw-r--r--   1 root root    21 2008-01-16 02:57 httpd.conf
drwxr-xr-x   2 root root  4096 2008-01-16 02:41 mods-available
drwxr-xr-x   2 root root  4096 2008-01-16 02:41 mods-enabled
-rw-r--r--   1 root root    59 2007-10-04 17:42 ports.conf
drwxr-xr-x   2 root root  4096 2008-01-16 02:36 sites-available
drwxr-xr-x   2 root root  4096 2008-01-16 03:10 sites-enabled

/etc/apache2/conf.d:
total 12
drwxr-xr-x 2 root root 4096 2008-01-16 02:36 .
drwxr-xr-x 7 root root 4096 2008-01-16 02:59 ..
-rw-r--r-- 1 root root  269 2007-10-04 17:42 charset

/etc/apache2/mods-available:
total 352
drwxr-xr-x 2 root root 4096 2008-01-16 02:41 .
drwxr-xr-x 7 root root 4096 2008-01-16 02:59 ..
-rw-r--r-- 1 root root  332 2007-10-04 17:42 actions.conf
-rw-r--r-- 1 root root   66 2007-10-04 17:42 actions.load
-rw-r--r-- 1 root root  815 2007-10-04 17:42 alias.conf
-rw-r--r-- 1 root root   62 2007-10-04 17:42 alias.load
-rw-r--r-- 1 root root   60 2007-10-04 17:42 asis.load
-rw-r--r-- 1 root root   72 2007-10-04 17:42 auth_basic.load
-rw-r--r-- 1 root root   74 2007-10-04 17:42 auth_digest.load
-rw-r--r-- 1 root root   74 2007-10-04 17:42 authn_alias.load
-rw-r--r-- 1 root root   72 2007-10-04 17:42 authn_anon.load
-rw-r--r-- 1 root root   85 2007-10-04 17:42 authn_dbd.load
-rw-r--r-- 1 root root   70 2007-10-04 17:42 authn_dbm.load
-rw-r--r-- 1 root root   78 2007-10-04 17:42 authn_default.load
-rw-r--r-- 1 root root   72 2007-10-04 17:42 authn_file.load
-rw-r--r-- 1 root root   90 2007-10-04 17:42 authnz_ldap.load
-rw-r--r-- 1 root root   70 2007-10-04 17:42 authz_dbm.load
-rw-r--r-- 1 root root   78 2007-10-04 17:42 authz_default.load
-rw-r--r-- 1 root root   82 2007-10-04 17:42 authz_groupfile.load
-rw-r--r-- 1 root root   72 2007-10-04 17:42 authz_host.load
-rw-r--r-- 1 root root   74 2007-10-04 17:42 authz_owner.load
-rw-r--r-- 1 root root   72 2007-10-04 17:42 authz_user.load
-rw-r--r-- 1 root root 2335 2007-10-04 17:42 autoindex.conf
-rw-r--r-- 1 root root   70 2007-10-04 17:42 autoindex.load
-rw-r--r-- 1 root root   62 2007-10-04 17:42 cache.load
-rw-r--r-- 1 root root   70 2007-10-04 17:42 cern_meta.load
-rw-r--r-- 1 root root   68 2007-10-04 17:42 cgid.conf
-rw-r--r-- 1 root root   60 2007-10-04 17:42 cgid.load
-rw-r--r-- 1 root root   58 2007-10-04 17:42 cgi.load
-rw-r--r-- 1 root root   76 2007-10-04 17:42 charset_lite.load
-rw-r--r-- 1 root root   36 2007-10-04 17:42 dav_fs.conf
-rw-r--r-- 1 root root   79 2007-10-04 17:42 dav_fs.load
-rw-r--r-- 1 root root   58 2007-10-04 17:42 dav.load
-rw-r--r-- 1 root root   68 2007-10-04 17:42 dav_lock.load
-rw-r--r-- 1 root root   58 2007-10-04 17:42 dbd.load
-rw-r--r-- 1 root root  107 2007-10-04 17:42 deflate.conf
-rw-r--r-- 1 root root   66 2007-10-04 17:42 deflate.load
-rw-r--r-- 1 root root  112 2007-10-04 17:42 dir.conf
-rw-r--r-- 1 root root   58 2007-10-04 17:42 dir.load
-rw-r--r-- 1 root root  475 2007-10-04 17:42 disk_cache.conf
-rw-r--r-- 1 root root   89 2007-10-04 17:42 disk_cache.load
-rw-r--r-- 1 root root   64 2007-10-04 17:42 dump_io.load
-rw-r--r-- 1 root root   58 2007-10-04 17:42 env.load
-rw-r--r-- 1 root root   66 2007-10-04 17:42 expires.load
-rw-r--r-- 1 root root   72 2007-10-04 17:42 ext_filter.load
-rw-r--r-- 1 root root   89 2007-10-04 17:42 file_cache.load
-rw-r--r-- 1 root root   64 2007-10-04 17:42 filter.load
-rw-r--r-- 1 root root   66 2007-10-04 17:42 headers.load
-rw-r--r-- 1 root root   62 2007-10-04 17:42 ident.load
-rw-r--r-- 1 root root   68 2007-10-04 17:42 imagemap.load
-rw-r--r-- 1 root root   66 2007-10-04 17:42 include.load
-rw-r--r-- 1 root root  420 2007-10-04 17:42 info.conf
-rw-r--r-- 1 root root   60 2007-10-04 17:42 info.load
-rw-r--r-- 1 root root   60 2007-10-04 17:42 ldap.load
-rw-r--r-- 1 root root   76 2007-10-04 17:42 log_forensic.load
-rw-r--r-- 1 root root  185 2007-10-04 17:42 mem_cache.conf
-rw-r--r-- 1 root root   87 2007-10-04 17:42 mem_cache.load
-rw-r--r-- 1 root root 6279 2007-10-04 17:42 mime.conf
-rw-r--r-- 1 root root   60 2007-10-04 17:42 mime.load
-rw-r--r-- 1 root root   89 2007-10-04 17:42 mime_magic.conf
-rw-r--r-- 1 root root   72 2007-10-04 17:42 mime_magic.load
-rw-r--r-- 1 root root  663 2007-10-04 17:42 negotiation.conf
-rw-r--r-- 1 root root   74 2007-10-04 17:42 negotiation.load
-rw-r--r-- 1 root root  133 2008-01-10 03:38 php5.conf
-rw-r--r-- 1 root root   59 2008-01-10 03:38 php5.load
-rw-r--r-- 1 root root   87 2007-10-04 17:42 proxy_ajp.load
-rw-r--r-- 1 root root  103 2007-10-04 17:42 proxy_balancer.load
-rw-r--r-- 1 root root  589 2007-10-04 17:42 proxy.conf
-rw-r--r-- 1 root root   95 2007-10-04 17:42 proxy_connect.load
-rw-r--r-- 1 root root   87 2007-10-04 17:42 proxy_ftp.load
-rw-r--r-- 1 root root   89 2007-10-04 17:42 proxy_http.load
-rw-r--r-- 1 root root   62 2007-10-04 17:42 proxy.load
-rw-r--r-- 1 root root   66 2007-10-04 17:42 rewrite.load
-rw-r--r-- 1 root root 1122 2007-10-04 17:42 setenvif.conf
-rw-r--r-- 1 root root   68 2007-10-04 17:42 setenvif.load
-rw-r--r-- 1 root root   66 2007-10-04 17:42 speling.load
-rw-r--r-- 1 root root 2158 2007-10-04 17:42 ssl.conf
-rw-r--r-- 1 root root   58 2007-10-04 17:42 ssl.load
-rw-r--r-- 1 root root  398 2007-10-04 17:42 status.conf
-rw-r--r-- 1 root root   64 2007-10-04 17:42 status.load
-rw-r--r-- 1 root root   64 2007-10-04 17:42 suexec.load
-rw-r--r-- 1 root root   70 2007-10-04 17:42 unique_id.load
-rw-r--r-- 1 root root  293 2007-10-04 17:42 userdir.conf
-rw-r--r-- 1 root root   66 2007-10-04 17:42 userdir.load
-rw-r--r-- 1 root root   70 2007-10-04 17:42 usertrack.load
-rw-r--r-- 1 root root   66 2007-10-04 17:42 version.load
-rw-r--r-- 1 root root   74 2007-10-04 17:42 vhost_alias.load

/etc/apache2/mods-enabled:
total 8
drwxr-xr-x 2 root root 4096 2008-01-16 02:41 .
drwxr-xr-x 7 root root 4096 2008-01-16 02:59 ..
lrwxrwxrwx 1 root root   28 2008-01-16 02:36 alias.conf -> ../mods-available/alias.conf
lrwxrwxrwx 1 root root   28 2008-01-16 02:36 alias.load -> ../mods-available/alias.load
lrwxrwxrwx 1 root root   33 2008-01-16 02:36 auth_basic.load -> ../mods-available/auth_basic.load
lrwxrwxrwx 1 root root   33 2008-01-16 02:36 authn_file.load -> ../mods-available/authn_file.load
lrwxrwxrwx 1 root root   36 2008-01-16 02:36 authz_default.load -> ../mods-available/authz_default.load
lrwxrwxrwx 1 root root   38 2008-01-16 02:36 authz_groupfile.load -> ../mods-available/authz_groupfile.load
lrwxrwxrwx 1 root root   33 2008-01-16 02:36 authz_host.load -> ../mods-available/authz_host.load
lrwxrwxrwx 1 root root   33 2008-01-16 02:36 authz_user.load -> ../mods-available/authz_user.load
lrwxrwxrwx 1 root root   32 2008-01-16 02:36 autoindex.conf -> ../mods-available/autoindex.conf
lrwxrwxrwx 1 root root   32 2008-01-16 02:36 autoindex.load -> ../mods-available/autoindex.load
lrwxrwxrwx 1 root root   26 2008-01-16 02:41 cgi.load -> ../mods-available/cgi.load
lrwxrwxrwx 1 root root   26 2008-01-16 02:36 dir.conf -> ../mods-available/dir.conf
lrwxrwxrwx 1 root root   26 2008-01-16 02:36 dir.load -> ../mods-available/dir.load
lrwxrwxrwx 1 root root   26 2008-01-16 02:36 env.load -> ../mods-available/env.load
lrwxrwxrwx 1 root root   27 2008-01-16 02:36 mime.conf -> ../mods-available/mime.conf
lrwxrwxrwx 1 root root   27 2008-01-16 02:36 mime.load -> ../mods-available/mime.load
lrwxrwxrwx 1 root root   34 2008-01-16 02:36 negotiation.conf -> ../mods-available/negotiation.conf
lrwxrwxrwx 1 root root   34 2008-01-16 02:36 negotiation.load -> ../mods-available/negotiation.load
lrwxrwxrwx 1 root root   27 2008-01-16 02:41 php5.conf -> ../mods-available/php5.conf
lrwxrwxrwx 1 root root   27 2008-01-16 02:41 php5.load -> ../mods-available/php5.load
lrwxrwxrwx 1 root root   31 2008-01-16 02:36 setenvif.conf -> ../mods-available/setenvif.conf
lrwxrwxrwx 1 root root   31 2008-01-16 02:36 setenvif.load -> ../mods-available/setenvif.load
lrwxrwxrwx 1 root root   29 2008-01-16 02:36 status.conf -> ../mods-available/status.conf
lrwxrwxrwx 1 root root   29 2008-01-16 02:36 status.load -> ../mods-available/status.load

/etc/apache2/sites-available:
total 16
drwxr-xr-x 2 root root 4096 2008-01-16 02:36 .
drwxr-xr-x 7 root root 4096 2008-01-16 02:59 ..
-rw-r--r-- 1 root root 1183 2007-10-04 17:54 default
-rw-r--r-- 1 root root 1252 2008-01-16 03:10 lobo-tuerto

/etc/apache2/sites-enabled:
total 8
drwxr-xr-x 2 root root 4096 2008-01-16 03:10 .
drwxr-xr-x 7 root root 4096 2008-01-16 02:59 ..
lrwxrwxrwx 1 root root   40 2008-01-16 02:40 lobo-tuerto -> /etc/apache2/sites-available/lobo-tuerto
```

I think it's important to note, that I solved the problem about Apache2 not creating config files at install (maybe the purge option and the large list of packages I used helped there).

I think this problem is related to the Apache2 config, because accessing a page with php code in it would show it BLANK, but if I see the source code, the php code is there, it's just not parsed by the server. Maybe the modules aren't configured well?

Do you know which and where are the files I would need to configure?

---

### Post by lobo-tuerto on 2008-01-16
I don't know if this can help, but I've got another PC by my side, and I just installed Apache2 and PHP5 with:

```
sudo apt-get install apache2
```
```
sudo apt-get install php5
```

And it IS working...


Anyone know what should I copy from that machine to get my version up and running? or what configuration files should I compare? I don't know where to start looking even... :confused:

---

### Post by hyper_ch on 2008-01-16
```

sudo a2enmod php5

```

---

### Post by lobo-tuerto on 2008-01-16
> This module is already enabled!

:confused:


Btw I compared the /etc/php5 and /etc/apache2 from the working machine to this one, and there is NO difference.
:confused::confused:

---

### Post by hyper_ch on 2008-01-16
```

sudo /etc/init.d/apache2 restart

```

---

### Post by lobo-tuerto on 2008-01-16
I have been doing that all the way until here. I know I have to restart the server everytime I make a modification to something.

But you know what's weird, whenever I type this:

```
sudo /etc/init.d/apache2 restart
```

I'm getting this:
>  * Restarting web server apache2                                                
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName                                                                    [ OK ]


On the other machine (with the working server and php), I'm getting just one notification about "apache2: Could not reliably determine the server's fully qualified domain name". In this machine I'm getting 2, as if something was being processed twice. What do you think?

---

### Post by scizzo on 2008-01-16
> **lobo-tuerto said:**
> I have been doing that all the way until here. I know I have to restart the server everytime I make a modification to something.

But you know what's weird, whenever I type this:

```
sudo /etc/init.d/apache2 restart
```

I'm getting this:


On the other machine (with the working server and php), I'm getting just one notification about "apache2: Could not reliably determine the server's fully qualified domain name". In this machine I'm getting 2, as if something was being processed twice. What do you think?

127.0.1.1 ?

shouldn't it be 127.0.0.1?

and is that really a valid servername?

---

### Post by lobo-tuerto on 2008-01-16
That's ok, 127.0.1.1 maps to my localhost too (127.0.0.1).

Besides that's not the problem at all, as I said, I just installed Apache2 and PHP5 in my other PC, I'm getting the same message (just once, not double like in this one) but it's working as expected (the other PC IS parsing the php files).

---

### Post by lobo-tuerto on 2008-01-16
I'm going to be very pissed off if what I have read in this post is true:
[http://ubuntuforums.org/showpost.php?p=1319288&postcount=33](http://ubuntuforums.org/showpost.php?p=1319288&postcount=33)

I hope it doesn't hold true anymore
:(

---

### Post by scizzo on 2008-01-16
```
dpkg -l | grep libapache2-mod-php5
```

That package is installed?

---

### Post by lobo-tuerto on 2008-01-16
Jesus ******* Christ!

I know now why all the threads that have this problem suddenly die, with no answers lol

I'm going to confess, so others may learn, I mistyped the php tags... sorry ALL

I was writing <php? phpinfo(); ?> instead of <?php phpinfo(); ?>

Shame on me :(

P.D. Lesson learned, glad it happened now, and not in a difficult situation.

---


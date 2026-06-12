---
title: "problems getting drupal installed"
date: 2008-02-27
forum: Absolute Beginner Talk
---

### Post by benfindlay on 2008-02-27
Hi guys, looked for this problem on the forums and not sure if anyone has come across it yet. I've been trying to install drupal following the guide here: [https://help.ubuntu.com/community/Drupal]("https://help.ubuntu.com/community/Drupal")
All goes well, but when I get the the stage where you type ```
http://localhost/drupal/
``` into your browser, it just prompts me to open/save a file, as if its trying to download something (see screenshot) Am I being totally daft here and missing something obvious?

Thanks in advance!

Ben

---

### Post by kaens on 2008-02-27
Looks like apache isn't running, or php isn't installed correctly.

Do a sudo /etc/init.d/apache2 restart again.

If that doesnt work, what happens when you go to just [http://localhost?](http://localhost?)

---

### Post by benfindlay on 2008-02-27
Putting localhost into the browser displays the temporary holding page I've put into /var/www/ just so that it doesnt have a blank page. Does that mean that it's php that is the problem?

---

### Post by kaens on 2008-02-27
You did install libapache2-mod-php5?  What's the output of

```

apache2 -M

```

---

### Post by benfindlay on 2008-02-28
It doesn't recognise the command > apache2 -M
says illegal option

Also when I tried to restart apache2 with > sudo /etc/init.d/apache2 restart I get the following:
> $ sudo /etc/init.d/apache2 restart
 * Forcing reload of apache 2.0 web server...
apache2: Could not determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
apache2: Could not determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
   ...done.

Could this be the problem?

---

### Post by kaens on 2008-02-28
The message about the fully qualified domain name is normal, that's not the problem.

apache2 -M should list the modules loaded into apache2. It should _not_ give you an invalid option error. It's synonymous with the following command:

```

apache2 -t -D DUMP_MODULES

```

Does that work?

---

### Post by benfindlay on 2008-02-29
that command gives me
> $ apache2 -t -D DUMP_MODULES
apache2: Could not determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
Syntax OK


---

### Post by kaens on 2008-02-29
Okay, it looks like absolutely no modules are loaded into apache, which isn't correct. Let's see if we can't figure this out (I'm frankly just as confused as you are as to why this is going on, especially if you followed that howto exactly).

What are the contents of the folder /etc/apache2/mods-available/ ?

Also, what are the contents if any (I suspect not though) of /etc/apache2/mods-enabled/ ?

---

### Post by benfindlay on 2008-02-29
Mods-available contains the following:
> :/etc/apache2/mods-available$ ls
actions.load      dav_fs.load      mem_cache.load      rewrite.load
asis.load         dav.load         mime_magic.conf     speling.load
auth_anon.load    deflate.load     mime_magic.load     ssl.conf
auth_dbm.load     disk_cache.load  php4.conf           ssl.load
auth_digest.load  expires.load     php4.load           suexec.load
auth_ldap.load    ext_filter.load  php5.conf           unique_id.load
cache.load        file_cache.load  php5.load           userdir.conf
cern_meta.load    headers.load     proxy.conf          userdir.load
cgid.conf         imap.load        proxy_connect.load  usertrack.load
cgid.load         include.load     proxy_ftp.load      vhost_alias.load
cgi.load          info.load        proxy_http.load
dav_fs.conf       ldap.load        proxy.load


Mods-enabled contains this:
> :/etc/apache2/mods-enabled$ ls
cgi.load  userdir.conf  userdir.load


Cheers
Ben

---

### Post by kaens on 2008-02-29
Alright, try this:

```

$ cd /etc/apache2/
$ ln -s mods-available/php5.conf mods-enabled/php5.conf
$ ln -s mods-available/php5.load mods-enabled/php5.load
$ apache2ctl restart

```

This should load the php5 module into apache, and then hopefully it will be working as expected.

---


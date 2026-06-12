---
title: "Please explain Wordpress Community Docs Instructions"
date: 2007-08-20
forum: Absolute Beginner Talk
---

### Post by mahalie on 2007-08-20
My previous attempts involved just putting the extracted WP package in my chosen dir via FTP and then creating the DB and user and creating a config file. Unfortunately I got a weird 'forbidden' error. It seems to be some sort of apache config. Reading apache forums, wordpress forums etc to figure it out hasn't helped me so I thought I'd try doing it the 'official docs' way before asking for help. But now I need help with the Ubuntu Community Docs directions!!

I don't understand all of the instructions given on the [Wordpress page]("https://help.ubuntu.com/community/WordPress") of the Community Docs.
[https://help.ubuntu.com/community/WordPress](https://help.ubuntu.com/community/WordPress)

Specifically this section:
```
sudo ln -s /usr/share/wordpress /var/www/wordpress 
sudo sh /usr/share/doc/wordpress/examples/setup-mysql -n (your mysql user) localhost 
sudo /etc/init.d/apache2 restart
```

[LIST]
[*]First, why create a link instead of just moving the wordpress files? (I put the tar.gz in my home directory and then extracted it the location I wanted in /var/www/blogname.
[*]This makes the second line really confusing (to me). 'sudo sh' means to do the following commands as admin right? I don't have a directory names 'examples' and not sure at all what this line is doing. I have already tried installing WP a few times using other directions and most of them use phpMyAdmin for setting up DB. According to where I put the WP files (/var/www/blogname) what would I change the middle command to?
[/LIST]

I'm trying really hard to do this all using the CLI, by the way. LAMP server install Ubuntu Dapper Drake 6.06 LTS. Apache admin newb in addition to an Ubuntu newb. Recipe for disaster? Prolly.

---

### Post by Ek0nomik on 2007-08-20
You said this doesn't work?

[http://codex.wordpress.org/Installing_WordPress#Famous_5-Minute_Install](http://codex.wordpress.org/Installing_WordPress#Famous_5-Minute_Install)

They may have created the link so if you accidentally delete your folder containing the link, you don't actually delete the wordpress files, rather just the link itself.

---

### Post by Jimmyfj on 2007-08-20
Did you remember to chmod the rights on the FTP/WP folder you chose? I Usually set my chmod to 755  -  and 777 for install and config.

---

### Post by mahalie on 2007-08-20
OK! I still don't understand the Community Docs Wordpress instructions but no matter. Finally figured it out. In my case I was putting the blog in /var/blogs/blogname/. I had to CHMOD both the directory 'blogs' and 'blogname' to 755 to get it to work.

---

### Post by jakaspaka on 2007-09-18
The Docs are confusing and inadequate. I used the following steps :
(I assume that you know how to configure Apache virtual host and MySql user and database and that you have LAMP up & running.)

Install WP from the repositories (rather than downloading):
```

sudo apt-get install wordpress
```

that installs wordpress in /usr/share/wordpress
and creates dir /etc/wordpress with two files in it

The trick here is to link your web folder to WP installation dir. You can link as many web folders to WP install dir thus making it centralized installation. Any upgrades and patches are then simplified and there is no need for copying or downloading files for each instance of blog on your server.

Apache dir is usually in /var/www, so: symbolic link from apache dir to WP install dir
```

sudo ln -s /usr/share/wordpress /var/www/blog.example.com
```

However, now you've got centralized config files also and that is a bit deferent from regular WP installation. That is why WP-settings are done with a little hack. if you look at the /usr/share/wordpress$ there is symbolic link (do not edit it)
```

wp-config.php -> /etc/wordpress/wp-config.php  
```
that has this line in it

```

require_once('/etc/wordpress/config-'.strtolower($_SERVER['HTTP_HOST']).'.php');
```

so what we need to do here is edit / create config file in /etc/wordpress with the name of our domaine in it (blog.example.com)

```

sudo joe config-blog.example.com.php
```

and insert standard WP config code in it.

As far as .htaccess file

```

# For rewrite rules needed for making Wordpress URL friendly
# See Options -> Permalinks for details and please use the defaults,
# especially in mind when hosting several blogs on one machine!
```

Correct me if I'm wrong, I guess standard Debian install does not provide a solution for permalinks. This basically means that you can't use them. WP will run with default options for permalinks. In many cases thats just fine. Nevertheless I'll be glad to see some update on this.

That's it. Plugins and themes can allso be done in similar way by symbolic linking or you can just put all the stuf in /usr/share/wordpress/wp-content dir. That would make plugins centralized also, and that's cool :)

---


---
title: "Getting wordpress to install"
date: 2007-10-09
forum: Absolute Beginner Talk
---

### Post by mohnkern on 2007-10-09
I've got apache 2 installed correctly, along with several applications, then I went to install wordpress with 

apt-get install wordpress

and then did the sudo ln -s /usr/share/wordpress /var/www/wordpress 

But sudo sh /usr/share/doc/wordpress/examples/setup-mysql -n root localhost   gives me a "bad substitution" error.

and there's no directory /usr/share/doc/wordpress

Tried dpkg --configure wordpress and it says it's installed and configured.

I'm sure I'm missing some critical step that isn't in [https://help.ubuntu.com/community/WordPress](https://help.ubuntu.com/community/WordPress)


If I go to [http://localhost/wordpress](http://localhost/wordpress) I get the following:

arning: require_once(/etc/wordpress/config-home.mohnkern.com.php) [function.require-once]: failed to open stream: No such file or directory in /etc/wordpress/wp-config.php on line 6

Fatal error: require_once() [function.require]: Failed opening required '/etc/wordpress/config-home.mohnkern.com.php' (include_path='.:/usr/share/php:/usr/share/pear') in /etc/wordpress/wp-config.php on line 6

---

### Post by rubbsdecvik on 2007-10-09
I did this a long time ago, on a computer that I don't use anymore, but I think this is what I ended up doing.

I actually just downloaded the source stuff from the website, and dropped the whole framework into my www folder.  From there I could configure it.  I'm pretty sure that worked better than the apt-get method.

Just an idea.

---

### Post by llamakc on 2007-10-09
Make sure you didn't make a typo when trying to get to /usr/share/doc/wordpress

It is there for me.

Here's the contents of /usr/share/doc/wordpress/examples/apache.conf

```

# There are about 3 ways to do this in Apache. In order of preference:

########## Virtual host VirtualDocumentRoot

NameVirtualHost *:80

<VirtualHost *:80>
UseCanonicalName    Off
VirtualDocumentRoot /var/www/%0
Options All
</VirtualHost>

#And then link the blog to your preferred domain, e.g.:
#ln -s /usr/share/wordpress /var/www/blog.example.com

#Of course make sure that the domain name 'blog.example.com' resolves to your
#local machine.

#################################
########## A defined Virtual host

NameVirtualHost *:80

<VirtualHost *:80>
VirtualDocumentRoot /usr/share/wordpress/
ServerName blog.example.com
ErrorLog /var/log/apache/wp-error.log
TransferLog /var/log/apache/wp-access.log
</VirtualHost>

########## Without using Virtual host, hosted off /blog

Alias /blog /usr/share/wordpress
<Directory /usr/share/wordpress>
  Options FollowSymLinks
  AllowOverride Limit Options FileInfo
  DirectoryIndex index.php
</Directory>
########## Tips
### If permalinks or rewrite is not working you probably need:
<Directory />
   Options FollowSymLinks
   AllowOverride All
</Directory>
# In your httpd.conf

### If NameVirtualHost *:80 is not working
You probably need to replace the * with the actual IP or hostname


```

Don't forget to run the sql setup script in /usr/share/doc/wordpress/examples/

#And then link the blog to your preferred domain, e.g.:
#ln -s /usr/share/wordpress /srv/www/blog.example.com

#Of course make sure that the domain name 'blog.example.com' resolves to your
#local machine.

---

### Post by mohnkern on 2007-10-10
I took the path of least resistance, and removed it using apt and then downloaded Wordpress from their web site and installed it, and it worked right out of the box.

---


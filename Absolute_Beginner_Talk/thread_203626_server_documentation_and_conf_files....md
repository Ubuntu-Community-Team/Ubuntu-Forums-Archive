---
title: "server documentation and conf files..."
date: 2006-06-25
forum: Absolute Beginner Talk
---

### Post by kpm on 2006-06-25
I am new to this on a Linux machine... I just installed the Ubuntu LAMP server 6.06  and am reading through the server documentation here:
[https://help.ubuntu.com/ubuntu/serverguide/C/httpd.html](https://help.ubuntu.com/ubuntu/serverguide/C/httpd.html)

I find it confusing because either I am reading the wrong documentation, the conf files have changed and the documentation has not kept up, or there is an assumption that the user is to add the directives noted.  If it is the last of these reasons, then some explicit statement to that should be added as other directives are disscussed in the same manner and do exist in the default conf file.

For instance, the documentation claims 
```
The ServerName directive is optional and specifies what FQDN your site should answer to. The default virtual host has no ServerName directive specified, so it will respond to all requests that do not match a ServerName directive in another virtual host. If you have just acquired the domain name ubunturocks.com and wish to host it on your Ubuntu server, the value of the ServerName directive in your virtual host configuration file should be ubunturocks.com. Add this directive to the new virtual host file you created earlier (/etc/apache2/sites-available/mynewsite). 
```

The Apache2 'default' conf file which one copies to be the 'mynewsite' conf file does not contain a directive called 'ServerName' that I can see.

The documentation then continues ```
You may also want your site to respond to www.ubunturocks.com, since many users will assume the www prefix is appropriate. Use the ServerAlias directive for this. You may also use wildcards in the ServerAlias directive. For example, ServerAlias *.ubunturocks.com  will cause your site to respond to any domain request ending in .ubunturocks.com.
```

Again, the default conf file contains no 'ServerAlias' directive.

The documentation goes on... ```
The DocumentRoot directive specifies where Apache should look for the files that make up the site. The default value is /var/www. No site is configured there, but if you uncomment the RedirectMatch directive in /etc/apache2/apache2.conf requests will be redirected to /var/www/apache2-default where the default Apache2 site awaits. Change this value in your site's virtual host file, and remember to create that directory if necessary!
```

But, the apache2.conf file has no 'DocumentRoot' directive, there is a ServerRoot directive, but no 'DocumentRoot'.

I am sure the reason for this is staring me right in the face, but I can't see it, so if anyone can set me straight, it would be appreciated.

Thanks

---


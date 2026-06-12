---
title: "Apache - how to change default folder location"
date: 2007-01-25
forum: Absolute Beginner Talk
---

### Post by JohnnyAvocado on 2007-01-25
I was hoping someone could clear something up for me. I have seen some articles that discuss this but can't seem to find the right solution.

I have a folder called "website1" sitting in the /var/www folder. How do I modify apache to default to the /var/www/website1 folder instead of just /var/www?

I have to manually enter [http://x.x.x.x/website1](http://x.x.x.x/website1) and would like to have it so that i just type [http://x.x.x.x](http://x.x.x.x)

Thanks so much for any help.

-Johnny

---

### Post by compiledkernel on 2007-01-25
[http://httpd.apache.org/docs/2.0/](http://httpd.apache.org/docs/2.0/)

A full bevy of docs there, should be able to find what you need and what.

---

### Post by punx45 on 2007-01-25
basically you want to go to your config file: 
in apache 1.3 the default is /etc/apache/httpd.conf
in apache2 the default is /etc/apache2/sites-available/default
(note that apache2 is virtual host based even if you are running only one site.   i suggest reading the apache docs linked above to make sure you know what you are doing.   docs for 1.3 are available on the apache.org site too.

search for the line that contains 'DocumentRoot' and change /var/www to /var/www/website1

of course, the simpler solution would be to just place your index.html file in /var/www rather than /var/www/website1

unless of course you are planning on hosting multiple websites (i.e. site1.com and site2.com) on the same machine, in which case you are barking up the wrong tree, and need to read up on configuring virtual hosts. (which appears to be easier in apache2)

---

### Post by kebes on 2007-01-25
If you have a standard apache 2 installation, I believe you can go to the file:
/etc/apache2/sites-available/default

In that file, you can either change the line:
DocumentRoot /var/www

to something else, like:
DocumentRoot /var/www/subfolder/


Alternately, you can find the subsection that looks like this:
```

        <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
                # Uncomment this directive is you want to see apache2's
                # default start page (in /apache2-default) when you go to /
                #RedirectMatch ^/$ /apache2-default/
        </Directory>

```

And uncomment the line that says "RedirectMatch" and change the "/apache2-default/" to whatever you want. So something like:
RedirectMatch ^/$ /subfolder/


In either case you'll need to restart your webserver by going:
/etc/init.d/apache2 restart


Hope that helps.

---

### Post by JohnnyAvocado on 2007-01-26
Punx45 / Kebes, I really, really appreciate both of your efforts. I had already tried the DocumentRoot modification approach but couldn't seem to get it to work. I do also understand the concept of virtual hosting as I have used IIS for several years and done it. It's just apache/linux is completely new to me. For the meantime I plan on just hosting 1 site. What I finally did was throw in a redirect for now (<meta http-equiv="refresh" content="0; URL=/website1">) which got the job done.

Kebes, I will have to give the RedirectMatch a try. 

Again, thank you both for your efforts. I'm close to getting the site up :)

If/when I do get it all figured out, I will update the post as I have seen a lot of people with the same problem.

---


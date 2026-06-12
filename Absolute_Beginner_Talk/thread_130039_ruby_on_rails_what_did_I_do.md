---
title: "ruby on rails: what did I do?"
date: 2006-02-15
forum: Absolute Beginner Talk
---

### Post by bbqbaker on 2006-02-15
Hi everyone, i just intalled ruby on rails by following this link:
[http://fo64.com/articles/2005/10/20/rails-on-breezy](http://fo64.com/articles/2005/10/20/rails-on-breezy)

and it seems that everything is working fine since I see the RoR output on my server. now I would really appreciate it if someone can help me understand what i did. here are my questions:

1. for the apache 2 configuration i did the following: what is it that I did?
```
#Go to the apache sites dir
cd /etc/apache2/sites-available
#Create a new config file for our site
sudo touch test

```
```
<VirtualHost *:80>
    ServerName *
    DocumentRoot /var/www/test/public/
    ErrorLog /var/log/apache2/error.log

    <Directory /var/www/test/public/>
      Options ExecCGI FollowSymLinks
      AddHandler cgi-script .cgi
      AllowOverride all
      Order allow,deny
      Allow from all

    </Directory>
  </VirtualHost>

```

```
cd /etc/apache2/sites-enabled
sudo rm 000-default
sudo ln -s ../sites-available/test ./test
sudo /etc/init.d/apache2 restart

```

2. I then created my first rails app by doing this: is this how the whole framework is created in rails?

```
cd /var/www
sudo rails test
cd test
sudo ruby script/generate controller pleasework

```

```
class PleaseworkController < ApplicationController
   def index
      render_text "if you see this you didn't just wast 20 minutes" 
   end
end

```

---


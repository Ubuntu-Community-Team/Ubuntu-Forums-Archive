---
title: "RoR on Fiesty/Edgy, Apache2, FCGI"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by threadhead on 2007-04-29
**Target:**
Ruby on Rails running on Apache2, FCGI from the /var/www directory. For Fiesty and Edgy.

I have been mashing my head for TWO days now trying to get a Ruby on Rail install to work on Fiesty with Apache2 and FCGI. It worked fine with the Mongrel built-in server, but since I would be moving the app to a production Apache2 server, I wanted to be as close to production as possible. I figured out my problems on why it wouldn't work and I hope this saves someone else a lot of aggravation.

**The Setup:**
First, I run my rails apps from the /var/www directory. This is the default directory that apache2 servers all files, so I have just stuck with it. VERY IMPORTANT: these instructions are for those who wish to keep your rails appls in the /var/www directory. If you are serving from your home directory, then you don't need this.

Install RoR just like everyone else says. The first part that hung me up was that I did not install libfcgi-ruby1.8. It will run with CGI just fine, but you will need this for FCGI.
```
sudo apt-get install libfcgi-ruby1.8
```

There is no need to modify your apache2.conf (even if someone tells you so).

I did not need to run as a virutal host, so I just just used an alias in the sites-available/default. You can add this to the end of the default, or create your own new site file (and enable it).
```
sudo pico /etc/apache2/sites-available/default

--append to the end

Alias /myApp /var/www/myApp/public
<Directory /var/www/myApp/public>
   Order allow,deny
   Allow from all
   AllowOverride all
</Directory>

```

Finally, this is the part that hung me up for so long, the permissions/owner of all your rails files need to be 'www-data' in order for apache2 to follow everything correctly. You see, when you remote into  your /var/www directory and run the rails scripts to do all the generation/scaffold/etc you need to sudo all the commands. This creates all the files with root ownership. The simple fix is to run this from your /var/www directory:
```
sudo chown -R www-data myApp
```

In the future, when you issue rails/ruby script commands, you can use 'sudo -u www-data' so that all the files that are created are created with www-data owner:
```
sudo -u www-data ruby script/generate scaffold myfoo myfoo
```

---

### Post by bloodniece on 2007-05-02
This is for Dapper but it worked for me on Feisty.
You have to compile FCGI from source for it to work.

[http://davidwinter.me.uk/articles/2006/08/09/ubuntu-dapper-web-server-how-to/](http://davidwinter.me.uk/articles/2006/08/09/ubuntu-dapper-web-server-how-to/)

---

### Post by HumanAnarchist on 2007-05-07
Nice, thanks for the effort 

-ha-

---


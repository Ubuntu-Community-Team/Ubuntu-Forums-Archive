---
title: "Could not reliably determine the server's fully qualified domain name, using 127.0.1,"
date: 2008-03-05
forum: Absolute Beginner Talk
---

### Post by ben22 on 2008-03-05
[B]In Short the problems:
Qualified domain name not f[LIST]
[*]ound - solved by chaning apache2.conf
[*]cannot open localhost, - tried
[/LIST] editing the /sites-available/default > NOT SOLVED
[/B]


Hello,

while installing apache 2 an error msg about a qualified domain name appeared:
```
 * Starting web server apache2                                                                                             apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
```
                                                                                                                    [ OK ]

According to other posts I added **ServerName "localhost"** to the apache2.conf and restarting apache2 made the error about qualified domain name vanish.



However, I still cannot open localhost to get the message "It works".

I edited the **/etc/apache2/sites-available/default** file and changed the Document Root and the default directory - NO SUCCESS:

```

[DocumentRoot /var/www/
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
**	<Directory /var/www/apache2-default>**
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
		# This directive allows us to have apache2's default start page
                # in /apache2-default/, but still have / go to the right place
                #RedirectMatch ^/$ /apache2-default/
	</Directory>
```

Removing the # did not help by the way.


Here also the data from the /etc/hosts:

127.0.0.1	localhost
127.0.1.1	ben-desktop

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

Bottomline: opening [http://localhost](http://localhost) does not show any page.

HELP VERY MUCH APPRECIATED!!


ben

---

### Post by halitech on 2008-03-05
will it load if you use 127.0.0.1?

---

### Post by ben22 on 2008-03-05
> **halitech said:**
> will it load if you use 127.0.0.1?

No, it doesnt

---

### Post by ben22 on 2008-03-05
> >  ben@ben-desktop:~$ sudo netstat -anp | grep '^tcp.*LISTEN'
> >  [sudo] password for ben:
> >  tcp        0      0 0.0.0.0:80              0.0.0.0:*
> >  LISTEN     5114/apache2

So apache is listening on port 80 of all IP addresses. This is as it should be.

Then why can't you connect? It could be any number of reasons, but
very few of them have anything to do with apache configuration. That
is why I again recommend you head over to a ubuntu forum where they
understand how your system is setup. You could have a firewall in
place. You could be connecting from the wrong machine. There could be
some deeper network configuration error on the box. I don't know.

Joshua.


This answer I got from Apache support.

Maybe some Ubuntu user can be of help.

---

### Post by Belak on 2008-05-30
Well, IDK if this will help, but with apache comes 2 relevant functions.

a2ensite
and a2dissite

My guess is that apache doesn't have a site enabled.

Is there anything in /etc/apache2/sites-enabled/ ?

If there isn't try running the following command
sudo a2ensite default

That will (In theory) enable the default site

Cheers,
Belak

---


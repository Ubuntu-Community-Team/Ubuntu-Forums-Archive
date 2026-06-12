---
title: "Apache error - server's fully qualified domain name"
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by Robynsveil on 2007-04-26
Hi,
I've installed Apache2 and php, and decided to test it. When I tried to do a re-start from Terminal, I got:
> robyn@Flight:~$ sudo /etc/init.d/apache2 restart
                                 * Forcing reload of web server (apache2)...
                                    apache2: Could not reliably determine the server's fully qualified domain name, using 
                                    127.0.0.1 for ServerName
                                    httpd (no pid file) not running
                                    apache2: Could not reliably determine the server's fully qualified
                                    domain name, using 127.0.0.1 for ServerName


My /etc/hosts file has:
> 
127.0.0.1 localhost Flight
127.0.1.1 Flight

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts


Where else do I need to be looking?

Thanks for replying - you're an awesome team!
Cheers
Robyn

---

### Post by Robynsveil on 2007-04-27
Doing a search this arvie on this issue took me to a thread that recommended I do:

```

robyn@Flight:~$ sudo netstat -anp | grep '^tcp.*LISTEN'

```
which yielded
> 
tcp        0      0 127.0.0.1:2208          0.0.0.0:*               LISTEN     4836/hpiod          
tcp        0      0 0.0.0.0:2049            0.0.0.0:*               LISTEN     -                   
tcp        0      0 0.0.0.0:930             0.0.0.0:*               LISTEN     5415/rpc.mountd     
tcp        0      0 0.0.0.0:901             0.0.0.0:*               LISTEN     5282/xinetd         
tcp        0      0 0.0.0.0:62570           0.0.0.0:*               LISTEN     6793/wish           
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN     4959/mysqld         
tcp        0      0 0.0.0.0:52623           0.0.0.0:*               LISTEN     5294/rpc.statd      
tcp        0      0 0.0.0.0:111             0.0.0.0:*               LISTEN     3989/portmap        
tcp        0      0 0.0.0.0:8081            0.0.0.0:*               LISTEN     5185/mono           
tcp        0      0 127.0.0.1:53            0.0.0.0:*               LISTEN     4764/named          
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     4812/cupsd          
tcp        0      0 127.0.0.1:953           0.0.0.0:*               LISTEN     4764/named          
tcp        0      0 0.0.0.0:36795           0.0.0.0:*               LISTEN     -                   
tcp        0      0 127.0.0.1:2207          0.0.0.0:*               LISTEN     4861/python         
tcp6       0      0 :::53                   :::*                    LISTEN     4764/named          
tcp6       0      0 ::1:953                 :::*                    LISTEN     4764/named

Not sure if I got this right, but in the fourth column - the third is just a column of 0s - there is that octet, some starting with 127... anyway, the number after the semi-colon is the port, right? So, port 80 isn't even occupied, and I can't see Apache running... 

...back to the exploration [head-down, bum-up]

---

### Post by Robynsveil on 2007-04-27
Well, this gets better and better. I thought I'd have a quick look in System -> Administration -> Services to see if any Apaches were running around... nobody was ticked. Seems I have Apache and Apache2 installed and ready to start as services - I remember they were both ticked at one point.
So, I issued a:
```
robyn@Flight:~$ sudo /etc/init.d/apache2 restart

```
which gave me:
> 
 * Forcing reload of web server (apache2)...                                                                          apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
httpd (no pid file) not running
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
                                                                                                               [ OK ]

...so I re-did a 
```

robyn@Flight:~$ sudo netstat -anp | grep '^tcp.*LISTEN'

```
which this time yielded:
> 
tcp        0      0 127.0.0.1:2208          0.0.0.0:*               LISTEN     4836/hpiod          
tcp        0      0 0.0.0.0:2049            0.0.0.0:*               LISTEN     -                   
tcp        0      0 0.0.0.0:930             0.0.0.0:*               LISTEN     5415/rpc.mountd     
tcp        0      0 0.0.0.0:901             0.0.0.0:*               LISTEN     5282/xinetd         
tcp        0      0 0.0.0.0:62570           0.0.0.0:*               LISTEN     6793/wish           
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN     4959/mysqld         
tcp        0      0 0.0.0.0:52623           0.0.0.0:*               LISTEN     5294/rpc.statd      
tcp        0      0 0.0.0.0:111             0.0.0.0:*               LISTEN     3989/portmap        
**[COLOR="Red"]tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN     10462/apache2[/COLOR]**       
tcp        0      0 0.0.0.0:8081            0.0.0.0:*               LISTEN     5185/mono           
tcp        0      0 127.0.0.1:53            0.0.0.0:*               LISTEN     4764/named          
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     4812/cupsd          
tcp        0      0 127.0.0.1:25            0.0.0.0:*               LISTEN     8615/exim4          
tcp        0      0 127.0.0.1:953           0.0.0.0:*               LISTEN     4764/named          
tcp        0      0 0.0.0.0:36795           0.0.0.0:*               LISTEN     -                   
tcp        0      0 127.0.0.1:2207          0.0.0.0:*               LISTEN     4861/python         
tcp6       0      0 :::53                   :::*                    LISTEN     4764/named          
tcp6       0      0 ::1:953                 :::*                    LISTEN     4764/named

So, based on what was returned from that first command, I got Apache2 *running* but sub-optimally because of the lack of a fully qualified domain name for the server. Think I'm on to something? anyone, feel free to jump in, here. :)

---

### Post by Cypher on 2007-04-27
Will you be accessing Apache locally or from within the network? If locally, you can direct Firefox to [http://localhost](http://localhost) and it will work no problem.

---

### Post by Calash on 2007-04-27
I get that error on mine, but Apache works fine so I have just been ignoring it.  From my understanding that setting is used if you have a domain name associated to that server.

Even with that error I can access the server fine from other systems on the network.

---

### Post by Robynsveil on 2007-04-27
> **Cypher said:**
> Will you be accessing Apache locally or from within the network? If locally, you can direct Firefox to [http://localhost](http://localhost) and it will work no problem.
Thanks Cypher... locally, for now. Eventually, I'll be setting up proper servers and workstations when I get my Linux-based proxy/NAT server up and running to access the Internet (as opposed to Window 2K-based ICS.

---

### Post by Robynsveil on 2007-04-27
> **Calash said:**
> I get that error on mine, but Apache works fine so I have just been ignoring it.  From my understanding that setting is used if you have a domain name associated to that server.

Even with that error I can access the server fine from other systems on the network.

Thanks Calash... and you are right - [http://localhost/phpinfo.php](http://localhost/phpinfo.php) *now* displays the php stuff, whereas before it wouldn't... so the problem (in my case at least) was trying to run two instances/versions of Apache.

---

### Post by Forgott3n on 2007-04-29
The answer is in your apache2.conf

you need to add the line ```
ServerName "YourSite.com"
``` in order for the message to go away.

---

### Post by useLinux, on 2007-04-29
I submitted a few posts but no-ones helping ;(. i added you to msn becuase you where doing something i am struggling too. The whole server thing.. :( Can you accept please. I would really appreciate if you could help me. :(

---

### Post by Robynsveil on 2007-04-29
> **useLinux, said:**
> I submitted a few posts but no-ones helping ;(. i added you to msn becuase you where doing something i am struggling too. The whole server thing.. :( Can you accept please. I would really appreciate if you could help me. :(
I'm not sure I'm a great resource - actually, I've found these boards a great support system. What I do now - as opposed to what I did when I first started this thread - is exhaustively research the question: all I do is click on 'Search' and type in a few key-words. True, you get a fair bit of fluff, and I never open any of the posts that don't have at least 1 response in them, but overall there hasn't been a question that wasn't answered, to some degree.
At this point, I'm trying to set up a proxy/NAT server. I was - on the recommendation of one of the blokes at my Linux user group - going to have a go with the distro ClarkConnect, but after it asked all the questions, did a blue-screen core dump with a 'panic' error... so I'm not real convinced I'll be using that.

Cheers...

---

### Post by Robynsveil on 2007-04-29
> **Forgott3n said:**
> The answer is in your apache2.conf

you need to add the line ```
ServerName "YourSite.com"
``` in order for the message to go away.

I'm using a peer-to-peer network ATM... shouldn't affect how other access my LAN website, right? Also, is there any particular place I should add the:
ServerName "YourSite.com"
in the /etc/apache2/apache2.conf? Like under ServerRoot, where it says:
ServerRoot "/etc/apache2"
??

Thanks for your replies!

---

### Post by useLinux, on 2007-04-30
I entered it under root and it was fine :) It didnt send me back the Apache error. Only problem is now that i have fully installed everything etc and can view it fine on [http://localhost](http://localhost) How do i make it so others can view it in a web browser?

---

### Post by Forgott3n on 2007-04-30
> **Robynsveil said:**
> I'm using a peer-to-peer network ATM... shouldn't affect how other access my LAN website, right? Also, is there any particular place I should add the:
ServerName "YourSite.com"
in the /etc/apache2/apache2.conf? Like under ServerRoot, where it says:
ServerRoot "/etc/apache2"
??

Thanks for your replies!

Works perfectly under localhost, lan, or outside the router. If you don't own a domain, just set it to your internal ip address. For example:

```
ServerName "192.168.1.123"
```

The theory behind the name is so apache can direct it's resources properly (I think). Now it makes no difference other than good practice and people will get "SiteName.com" instead of "Localhost" on various apache pages (errors, directory listings, etc.)

---

### Post by lexarrow on 2007-05-09
I got the same error "server's fully qualified domain name", but I solved it when I found out that my ISP changed my static address. Hope this helps someone.

---

### Post by mitairusu on 2007-10-19
Sorry, i gona try to contribute more "problem"...

 The system wide resolv method its determinated by the /etc/host.conf

 The host.conf say, "multi". This method try to resolv a host address with multiple methods,

 with /etc/hosts , with a nameserver , or nis server. ( im not sure the order. )

 Ok.

 The address 127.0.0.1, always its clalled or named "localhost".

 Now...

 Your other addresses , your LAN ip , you WAN ip, are registered on some of this files o nameservers ?

 if not. That is what are you skip.


 Sorry, my english its bad, like my internet conexion.



 Have nice day.




[ UnReg ] - 7h3 m17a1

I'm only i Linux User.

---

### Post by gazotem on 2008-01-03
try in terminal

gksudo gedit /etc/apache2/httpd.conf

add the line:
ServerName localhost

save the file.


then in terminal:
sudo /etc/init.d/apache2 restart

---

### Post by Quads on 2008-02-19
> **gazotem said:**
> try in terminal

gksudo gedit /etc/apache2/httpd.conf

add the line:
ServerName localhost

save the file.


then in terminal:
sudo /etc/init.d/apache2 restart

Winna!

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

### Post by xixsixxix on 2008-03-07
Ben, a note to begin with:

> According to other posts I added ServerName "localhost" to the apache2.conf and restarting apache2 made the error about qualified domain name vanish.

While I'm glad you got it working, in the future add to **/etc/apache2/httpd.conf** instead of apache2.conf. It has the same effect but allows you to keep your modifications separate from the default values.

Apache2 has things divided so you don't have to break the defaults to implement your own preferred settings. This also goes for the **/etc/apache2/sites-available/default** file. It should never be edited outside of removing the commented lines if you want to show the default Apache page.

If possible, revert your changes back to the original settings in default. If you want to edit it, make a  copy of the **default** file and link to your new file in **/etc/apache2/sites-enabled/**, like so:

```
$ cd /etc/apache2/sites-available
$ sudo cp default mysite

[...edit your mysite file with preferred settings...]

$ cd ../sites-enabled
$ sudo rm 000-default
$ sudo ln -s /etc/apache2/sites-available/mysite mysite
$ sudo /etc/init.d/apache2 restart
```

All that being said, it would appear that you're not matching up your directories. For now you should leave your settings to map to **/var/www**. If you want to show the default page, uncomment the *RedirectMatch* line. So your file [hopefully now called mysite :) ] should start off:

```
NameVirtualHost *
<VirtualHost *>
        ServerAdmin webmaster@localhost
        
        **DocumentRoot /var/www/**
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        **<Directory /var/www/>**
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
                # This directive allows us to have apache2's default start page
                # in /apache2-default/, but still have / go to the right place
                **RedirectMatch ^/$ /apache2-default/**
        </Directory>
```

...and then restart apache

```
$ sudo /etc/init.d/apache2 restart
```

Note that the first 2 bold lines both denote the Document Root and must match each other. It appears from:

> **DocumentRoot /var/www/**
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	**<Directory /var/www/apache2-default>**
	...

that you are essentially both skipping setting up access permissions for the DocumentRoot and never mapping to the apache2-default dir.

If that doesn't work for you, take Robyn's advice and run a netstat to check for apache2:

```
$ sudo netstat -anp | grep apache2
```

and see what port it's listed on. If there was a port conflict it may be running elsewhere, in which case you may need to direct your browser to that new port - e.g.: **[http://localhost:12345/](http://localhost:12345/)**

Your hosts file looks fine for your purposes, but if you want to be sure...

```
$ ping localhost
```

:)

---

### Post by meman on 2008-06-11
You have to change youre /etc/hosts file to:
```

127.0.0.1 localhost
127.0.1.1 Flight

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

---

### Post by albygil on 2008-06-12
> 
[quote]$ sudo /etc/init.d/apache2 restart
 * Restarting web server apache2
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
httpd (no pid file) not running
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
My /etc/hosts file has:
> 
Quote:
127.0.0.1 localhost [COLOR=Red]Flight[/COLOR]
127.0.1.1 Flight[/quote]I solved the problem simply erasing the duplicated alias in the first line. Apparently "/etc/hosts" can only map one FQDN per line.


regards

---

### Post by YourSurrogateGod on 2008-06-25
> **Robynsveil said:**
> Thanks Calash... and you are right - [http://localhost/phpinfo.php](http://localhost/phpinfo.php) *now* displays the php stuff, whereas before it wouldn't... so the problem (in my case at least) was trying to run two instances/versions of Apache.

I never got that far, this is what I get when I go to that URL:
> Not Found

The requested URL /phpinfo.php was not found on this server.
Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.1 with Suhosin-Patch Server at localhost Port 80

:/

This is my /etc/hosts file.
```
127.0.0.1	localhost
127.0.1.1	ysger

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

This is what happens when I do netstat.
```
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN      5143/mysqld     
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      7224/apache2    
tcp        0      0 0.0.0.0:8080            0.0.0.0:*               LISTEN      5337/beam       
tcp        0      0 127.0.0.1:40243         0.0.0.0:*               LISTEN      5337/beam       
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      5283/cupsd      
tcp        0      0 127.0.0.1:5432          0.0.0.0:*               LISTEN      5224/postgres   
tcp        0      0 127.0.0.1:41018         0.0.0.0:*               LISTEN      5545/ssl_esock  
tcp        0      0 0.0.0.0:8443            0.0.0.0:*               LISTEN      5545/ssl_esock  
```
I'm running 8.04.

When I try to restart apache2, it's fine. If only I could get phpinfo or phpmyadmin going...

[quote=Calash]I get that error on mine, but Apache works fine so I have just been ignoring it. From my understanding that setting is used if you have a domain name associated to that server.

Even with that error I can access the server fine from other systems on the network.[/quote]
Yeh, added the ServerName "FooBar.com" thing, doesn't do anything for the PHP stuff...

---

### Post by alizkhan on 2008-07-23
[B]Hey, I am getting the same error, I just installed Apache server on my computer and set it to maually start it for a user on port 8080. When I start apache from start menu. this is the error message i am getting in the error.log:
httpd.exe: Could not reliably determine the server's fully qualified domain name, using 130.63.84.72 for ServerName
[Wed Jul 23 13:29:19 2008] [notice] Apache/2.2.9 (Win32) configured -- resuming normal operations
[Wed Jul 23 13:29:19 2008] [notice] Server built: Jun 13 2008 04:04:59
[Wed Jul 23 13:29:19 2008] [notice] Parent: Created child process 3592
httpd.exe: Could not reliably determine the server's fully qualified domain name, using 130.63.84.72 for ServerName
Apache server shutdown initiated...
ine the server's fully qualified domain name, using 130.63.84.72 for ServerName
[Wed Jul 23 13:29:19 2008] [notice] Child 3592: Child process is running
[Wed Jul 23 13:29:19 2008] [notice] Child 3592: Acquired the start mutex.
[Wed Jul 23 13:29:19 2008] [notice] Child 3592: Starting 64 worker threads.
[Wed Jul 23 13:29:19 2008] [notice] Child 3592: Starting thread to listen on port 8080.
[Wed Jul 23 13:29:26 2008] [notice] Parent: Received shutdown signal -- Shutting down the server.
[Wed Jul 23 13:29:26 2008] [notice] Child 3592: Exit event signaled. Child process is ending.
[Wed Jul 23 13:29:27 2008] [notice] Child 3592: Released the start mutex
[Wed Jul 23 13:29:28 2008] [notice] Child 3592: All worker threads have exited.
[Wed Jul 23 13:29:28 2008] [notice] Child 3592: Child process is exiting
[Wed Jul 23 13:29:28 2008] [notice] Parent: Child process exited successfully.

Any help would be appreciated.[/B]

---


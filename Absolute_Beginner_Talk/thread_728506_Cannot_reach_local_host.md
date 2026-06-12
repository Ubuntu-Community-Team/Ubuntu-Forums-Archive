---
title: "Cannot reach local host"
date: 2008-03-18
forum: Absolute Beginner Talk
---

### Post by synistics on 2008-03-18
I have totally messed up something.

I was running Apache 2.2 with MySQL and a Drupal server.  I went to add two sub domains and messed something up.  Since then I am sure I have made things worse.  I need to get back to where I was so that I can finish the site and take it live.

Here are the logs I think people will need to look at to tell me where I totally messed it up!

-----------------------------------------------------------------------------
/etc/apache2/conf.d


-----------------------------------------------------------------------------

NameVirtualHost *
ServerName 127.0.0.1


------------------------------------------------------------------------------
------------------------------------------------------------------------------

/etc/apache2     ports.conf

--------------------------------------------------------------------------------

Listen 80

<IfModule mod_ssl.c>
    Listen 443
</IfModule>

--------------------------------------------------------------------------------
--------------------------------------------------------------------------------


/etc/apache2     httpd.conf

--------------------------------------------------------------------------------

empty....nothing....nada.......zip.....blank

--------------------------------------------------------------------------------
--------------------------------------------------------------------------------

host.conf

---------------------------------------------------------------------------------

# The "order" line is only used by old versions of the C library.
order hosts,bind
127.0.0.1     localhost.localdomain   localhost
192.168.2.6  server1.example.com     server1


----------------------------------------------------------------------------------
----------------------------------------------------------------------------------

hosts

----------------------------------------------------------------------------------

#127.0.0.1 localhost
#192.168.2.6 server1.example.com.@home server1
127.0.0.1       localhost.localdomain   localhost
192.168.2.6   server1.example.com     server1

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
127.0.0.1 [www.domainname.com](www.domainname.com) www2.domainname.com
127.0.0.1 [www.domainname.com](www.domainname.com) www2.domainname.com
127.0.0.1 [www.domainname.com](www.domainname.com) www2.domainname.com
127.0.0.1 [www.domainname.com](www.domainname.com) www2.domainname.com
127.0.0.1 [www.domainname.com](www.domainname.com) www2.domainname.com www3.domainname.com www4.domainname.com
127.0.0.1 [www.domainname.com](www.domainname.com) www2.domainname.com www3.domainname.com www4.domainname.com

----------------------------------------------------------------------------------
---------------------------------------------------------------------------------


error.log.1

---------------------------------------------------------------------------------------

/etc/host.conf: line 3: bad command `127.0.0.1       localhost.localdomain   localhost'
/etc/host.conf: line 4: bad command `192.168.0.4   server1.example.com     server1'
/etc/host.conf: line 3: bad command `127.0.0.1       localhost.localdomain   localhost'
/etc/host.conf: line 4: bad command `192.168.0.4   server1.example.com     server1'
/etc/host.conf: line 3: bad command `127.0.0.1       localhost.localdomain   localhost'
/etc/host.conf: line 4: bad command `192.168.0.4   server1.example.com     server1'
/etc/host.conf: line 3: bad command `127.0.0.1       localhost.localdomain   localhost'
/etc/host.conf: line 4: bad command `192.168.0.4   server1.example.com     server1'
/etc/host.conf: line 3: bad command `127.0.0.1       localhost.localdomain   localhost'
/etc/host.conf: line 4: bad command `192.168.0.4   server1.example.com     server1'
/etc/host.conf: line 3: bad command `127.0.0.1       localhost.localdomain   localhost'
/etc/host.conf: line 4: bad command `192.168.0.4   server1.example.com     server1'
/etc/host.conf: line 3: bad command `127.0.0.1       localhost.localdomain   localhost'
/etc/host.conf: line 4: bad command `192.168.0.4   server1.example.com     server1'
/etc/host.conf: line 3: bad command `127.0.0.1       localhost.localdomain   localhost'
/etc/host.conf: line 4: bad command `192.168.0.4   server1.example.com     server1'
/etc/host.conf: line 3: bad command `127.0.0.1       localhost.localdomain   localhost'
/etc/host.conf: line 4: bad command `192.168.0.4   server1.example.com     server1'
/etc/host.conf: line 3: bad command `127.0.0.1       localhost.localdomain   localhost'
/etc/host.conf: line 4: bad command `192.168.0.4   server1.example.com     server1'

-----------------------------------------------------------------------------------------
re-set the address to 192.168.0.6

-----------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------

both current error and access logs are blank

----------------------------------------------------------------------------------------
----------------------------------------------------------------------------------------

/etc/bind/db.local

----------------------------------------------------------------------------------------

;
; BIND data file for local loopback interface
;
$TTL	604800
@	IN	SOA	localhost. root.localhost. (
			      1		; Serial
			 604800		; Refresh
			  86400		; Retry
			2419200		; Expire
			 604800 )	; Negative Cache TTL
;
@	IN	NS	localhost.
@	IN	A	127.0.0.1

----------------------------------------------------------------------------------------
----------------------------------------------------------------------------------------

It will be something obvious, but I have gone through it step by step doing a re-config following the information at

[http://www.howtoforge.com/multisite_drupal_installation_ubuntu](http://www.howtoforge.com/multisite_drupal_installation_ubuntu)

and I continue to get the error message:

/etc/host.conf: line 3: bad command `127.0.0.1     localhost.localdomain   localhost'
/etc/host.conf: line 4: bad command `192.168.2.6  server1.example.com     server1'
PING [www.domainname.com](www.domainname.com) (127.0.0.1) 56(84) bytes of data.
64 bytes from localhost.localdomain (127.0.0.1): icmp_seq=1 ttl=64 time=0.043 ms
64 bytes from localhost.localdomain (127.0.0.1): icmp_seq=2 ttl=64 time=0.037 ms

--- [www.domainname.com](www.domainname.com) ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.037/0.040/0.043/0.003 ms

I have run through what I can find here and in other help sites, but nothing that I find seems to fix it and I am concerned I am just making a bigger mess of something that should be simple to do.

Thanks in advance

---

### Post by synistics on 2008-03-18
additional information:

domainname@server1:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:14:2A:67:99:9D  
          inet addr:192.168.2.6  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::214:2aff:fe67:999d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:31332 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17515 errors:0 dropped:0 overruns:0 carrier:0
          collisions:6535 txqueuelen:1000 
          RX bytes:36931882 (35.2 MB)  TX bytes:1442873 (1.3 MB)
          Interrupt:18 Base address:0xee00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:34 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1836 (1.7 KB)  TX bytes:1836 (1.7 KB)

domainname@server1:~$ netstat -r
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.2.0     *               255.255.255.0   U         0 0          0 eth0
link-local      *               255.255.0.0     U         0 0          0 eth0
/etc/host.conf: line 3: bad command `127.0.0.1     localhost.localdomain   localhost'
/etc/host.conf: line 4: bad command `192.168.2.6  server1.example.com     server1'
default         192.168.2.1     0.0.0.0         UG        0 0          0 eth0
domainname@server1:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.2.1     0.0.0.0         UG    100    0        0 eth0

thanks

---

### Post by synistics on 2008-03-18
bump

---

### Post by synistics on 2008-03-19
root@server1:/home/domainname# /etc/init.d/apache2 restart
 * Restarting web server apache2                                                Syntax error on line 7 of /etc/apache2/sites-enabled/www.domainname.com:
AllowOverride not allowed here
                                                                         [fail]

-------------------------------------------------------------------------------------------------

Virtual host file
-------------------------------------
<VirtualHost *>

		ServerAdmin [email]serverwebmaster@domainname.com[/email]
        DocumentRoot /var/www/drupal/sites/www.domainname.com
        
                Options FollowSymLinks
                AllowOverride None
        
        
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        
        ErrorLog /var/log/apache2/www.domainname.com/error.log
        LogLevel warn
        CustomLog /var/log/apache2/www.domainname.com/access.log combined
        ServerSignature Off

</VirtualHost>


I keep trying.... the solution must be somewhere here.

---

### Post by justanotherhandle on 2008-03-19
Well, it's really hard to offer advice when any number of things could have gone off when you were editing your configs.  I offer what I do to make a virtual host appear for local development to see if that helps.

1) edit the /etc/hosts to include the local routing. My /etc/hosts below with sample domain.

```
127.0.0.1       localhost
127.0.1.1       iceberg
127.0.0.1       DOMAINNAME.local

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```


2) added a file with the virtual host information to the /etc/apache2/sites-available/  File name used is DOMAINNAME.local and contents of DOMAINNAME.local is below.

```
NameVirtualHost *
<VirtualHost *>
        ServerAdmin webmaster@localhost
        ServerName www.DOMAINNAME.local
        ServerAlias DOMAINNAME.local
        DirectoryIndex index.html, index.php
        DocumentRoot ABSOLUTE/PATH/TO/LOCAL/DOMAIN/DOCUMENT/ROOT
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory ABSOLUTE/PATH/TO/LOCAL/DOMAIN/DOCUMENT/ROOT>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
                # This directive allows us to have apache2's default start page
                # in /apache2-default/, but still have / go to the right place
                #RedirectMatch ^/$ /apache2-default/
        </Directory>


        ErrorLog /var/log/apache2/error.log

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn

        CustomLog /var/log/apache2/access.log combined
        ServerSignature On
</VirtualHost>
```

3) created a symlink in /etc/apache2/sites-enabled. I named the symlink '00N-DOMAINNAME.local' (with N being any non-duplicate number of an existing file).

And viola. No messing with bind, no messing the http.conf (which is empty), and I can access the site on localhost via the url [http://DOMAINNAME.local/](http://DOMAINNAME.local/)

This is on Gutsy, but worked the same on my previous installation of Dapper.

If the configs are so messed that they are not recoverable ... then one (admittedly drastic) approach is to uninstall apache2, bind, whatever and then reinstall. As long as you have an idea of what other customizations you completed in your previous installation, you could just start fresh.

HTH

---

### Post by synistics on 2008-03-19
This may solve part but not all of the problem.

It still does not allow me to get to phpmyadmin, because of course, is cannot find the local server.

So frustrating, I am tempted to just delete and try a total re-install of apache.

Without the localhost or 127.0.0.1 accessible I am boxed in somewhat.


Thanks for the help so far.

---

### Post by justanotherhandle on 2008-03-19
Two different problems. 1) Setting up apache2 so that it "sees" and serves up virtual hosts locally, and 2) installing and accessing phpmyadmin

It's hard to help with 1) as I'm not sure how you've editing your configs, and all I can offer is how I did my configuration for locally served pages and hope that helped.  But for 2) Is apache2 running? If so, check if it is serving up it's default page by tying in the url 'http://localhost/' (no quotes). Does it work? if so, then apache is seeing localhost so that's not the problem and it's time to check how phpmyadmin was install/configured. 

HTH

---

### Post by synistics on 2008-03-19
Removed all of apache and conf files. Also needed to remove all Drupal and related conf and DB files to accomplish this. 

Reinstalled.

It is seeing the apache web page and the file directory.

I am still getting an error though as follows

 hostname -f

/etc/host.conf: line 3: bad command `127.0.0.1     localhost.localdomain   localhost'
/etc/host.conf: line 4: bad command `192.168.2.6  server1.example.com     server1'
server1.example.com

but it is working and viewable from one of the other computers.


Help is always appreciated when learning the hard way!

---

### Post by justanotherhandle on 2008-03-19
OK. Having apache serve up it's directory and default page is a good thing :)

I'm no networking guru, but I'm not seeing the need to include the local ip routing as part of the hosts, hostname, and host.conf subsystem. Again, I'm just making guesses as I can't be absolutely sure of what was changed on your end, so I'm giving you my hosts, hostname, and host.conf files in the hope that it will help.

**Contents of /etc/hosts. Note that here is no local routing ips, i.e., no ips which start with 192.168.0.0**
```
127.0.0.1       localhost
127.0.1.1       iceberg
127.0.0.1      DOMAINNAME.local

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

**Contents of /etc/hostname. Note that it contains ONLY the name of the local machine and no other routing information.**
```
MYLOGINNAME@iceberg:/etc$ cat /etc/hostname
iceberg
```

**Contents of /etc/host.conf. Note that there are no routing information AT ALL. **
```
MYLOGINNAME@iceberg:/etc$ cat /etc/host.conf
# The "order" line is only used by old versions of the C library.
order hosts,bind
multi on
```


Again, I'm no network guru, but I believe that the /etc/host.conf tells the local computer which databases to search for when presented with a network request, and if it finds a relevant entry in /etc/hosts it will use that. As an example, when presented with a request for localhost, it will first look to see which database to search, will search in find 'hosts' (the first entry in order in /etc/hosts.conf). Then if there is an entry for localhost in /etc/hosts find and dandy it will serve from 127.0.0.1 (the localhost ip). 

Same with serving up a domain which you are developing locally. If you are looking for DOMAINNAME.local, then the network request will first check to see which database it should look through to fullfill that request, determine that it should first look through /etc/hosts (the first database listed), to look for the DOMAINNAME.local. If it finds en entry for DOMAINNAME.local it will return that ip to the requesting service, in this case apache. Then it is up to the apache configuration to know where it should look for the DOMAINNAME.local files. The apache configuration files are in the /etc/apache2/sites-available and /etc/apache2/sites-enabled section.

HTH

---

### Post by synistics on 2008-03-19
the issue here is that I am following the step by step on installing a multi-site drupal service

[http://www.howtoforge.com/multisite_drupal_installation_ubuntu](http://www.howtoforge.com/multisite_drupal_installation_ubuntu)

had it up and running once before and then mucked it up when trying to add sub domains.

I am down to the small end of the list of steps and having issues with a line in virtual host as identified by the site names, right now there are four sites.

example one

<VirtualHost *>
	ServerAdmin [email]webadmin@sitename1.com[/email]
        DocumentRoot /var/www/drupal
        
                Options FollowSymLinks
                AllowOverride None
        
        
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        
        ErrorLog /var/log/apache2/error.log
        LogLevel warn
        CustomLog /var/log/apache2/access.log combined
        ServerSignature Off
</VirtualHost>

on the line:

              Allow Override None

I get the following error on the re-start of apache

root@server1:/etc/apache2/sites-enabled# /etc/init.d/apache2 restart
 * Restarting web server apache2                                                                                                                             Syntax error on line 6 of /etc/apache2/sites-enabled/www.sitename1.com:
AllowOverride not allowed here


This did not happen last time, so lost as to how or why this has been caused.

apache sites-available and enabled have the correct files in them with the site name.  

BTW, thanks for the discussion.

---

### Post by justanotherhandle on 2008-03-20
OK, it seems like we're bouncing from issue to issue. The first was unable to find localhost, which would be a setting up the network, i.e., the host(s) subsystem. So can I assume that the networking issue is resolved? Is the host(s) system working? Can you ping DOMAINNAME.local? If not, then the network is still a problem. 

If you can ping local domain, then now the issue would just be apache finding the domain, correct? From what you've posted, it looks like you're duplicating a few directives. This link is to the apache documentation on the directory and virtualhost directives. You might try placing the AllowOverrides in  separate directory directives.  See my apache local domain config posted earlier in the thread.
[http://httpd.apache.org/docs/2.0/mod/core.html#directory](http://httpd.apache.org/docs/2.0/mod/core.html#directory)
[http://httpd.apache.org/docs/2.0/mod/core.html#virtualhost](http://httpd.apache.org/docs/2.0/mod/core.html#virtualhost)

HTH

---


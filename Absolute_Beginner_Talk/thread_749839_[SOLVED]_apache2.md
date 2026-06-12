---
title: "[SOLVED] apache2"
date: 2008-04-08
forum: Absolute Beginner Talk
---

### Post by Daelakk on 2008-04-08
So I've just installed apache2 into Ubuntu 7.10 (or whatever the latest release is), and I've gone through the apache2.conf, but i can't edit anything- it says I don't have permission. I've set a password for root and tried to log on, but it gave me the message "can't log on to administrator from this screen" or something.
So I tried to start apache...
It gave me this:
```
jon@SHELL:~$ sudo /etc/init.d/apache2 restart
 * Restarting web server apache2                                                                 apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName

```

Although I cannot edit ServerName (or add it)
Here is my apache2.conf file:
```
#
# Based upon the NCSA server configuration files originally by Rob McCool.
#
# This is the main Apache server configuration file.  It contains the
# configuration directives that give the server its instructions.
# See http://httpd.apache.org/docs/2.2/ for detailed information about
# the directives.
#
# Do NOT simply read the instructions in here without understanding
# what they do.  They're here only as hints or reminders.  If you are unsure
# consult the online docs. You have been warned.  
#
# The configuration directives are grouped into three basic sections:
#  1. Directives that control the operation of the Apache server process as a
#     whole (the 'global environment').
#  2. Directives that define the parameters of the 'main' or 'default' server,
#     which responds to requests that aren't handled by a virtual host.
#     These directives also provide default values for the settings
#     of all virtual hosts.
#  3. Settings for virtual hosts, which allow Web requests to be sent to
#     different IP addresses or hostnames and have them handled by the
#     same Apache server process.
#
# Configuration and logfile names: If the filenames you specify for many
# of the server's control files begin with "/" (or "drive:/" for Win32), the
# server will use that explicit path.  If the filenames do *not* begin
# with "/", the value of ServerRoot is prepended -- so "/var/log/apache2/foo.log"
# with ServerRoot set to "" will be interpreted by the
# server as "//var/log/apache2/foo.log".
#

### Section 1: Global Environment
#
# The directives in this section affect the overall operation of Apache,
# such as the number of concurrent requests it can handle or where it
# can find its configuration files.
#

#
# ServerRoot: The top of the directory tree under which the server's
# configuration, error, and log files are kept.
#
# NOTE!  If you intend to place this on an NFS (or otherwise network)
# mounted filesystem then please read the LockFile documentation (available
# at <URL:http://httpd.apache.org/docs-2.1/mod/mpm_common.html#lockfile>);
# you will save yourself a lot of trouble.
#
# Do NOT add a slash at the end of the directory path.
#
ServerRoot "/etc/apache2"

#
# The accept serialization lock file MUST BE STORED ON A LOCAL DISK.
#
#<IfModule !mpm_winnt.c>
#<IfModule !mpm_netware.c>
LockFile /var/lock/apache2/accept.lock
#</IfModule>
#</IfModule>

#
# PidFile: The file in which the server should record its process
# identification number when it starts.
# This needs to be set in /etc/apache2/envvars
#
PidFile ${APACHE_PID_FILE}

#
# Timeout: The number of seconds before receives and sends time out.
#
Timeout 300

#
# KeepAlive: Whether or not to allow persistent connections (more than
# one request per connection). Set to "Off" to deactivate.
#
KeepAlive On

#
# MaxKeepAliveRequests: The maximum number of requests to allow
# during a persistent connection. Set to 0 to allow an unlimited amount.
# We recommend you leave this number high, for maximum performance.
#
MaxKeepAliveRequests 100

#
# KeepAliveTimeout: Number of seconds to wait for the next request from the
# same client on the same connection.
#
KeepAliveTimeout 15

##
## Server-Pool Size Regulation (MPM specific)
## 

# prefork MPM
# StartServers: number of server processes to start
# MinSpareServers: minimum number of server processes which are kept spare
# MaxSpareServers: maximum number of server processes which are kept spare
# MaxClients: maximum number of server processes allowed to start
# MaxRequestsPerChild: maximum number of requests a server process serves
<IfModule mpm_prefork_module>
    StartServers          5
    MinSpareServers       5
    MaxSpareServers      10
    MaxClients          150
    MaxRequestsPerChild   0
</IfModule>

# worker MPM
# StartServers: initial number of server processes to start
# MaxClients: maximum number of simultaneous client connections
# MinSpareThreads: minimum number of worker threads which are kept spare
# MaxSpareThreads: maximum number of worker threads which are kept spare
# ThreadsPerChild: constant number of worker threads in each server process
# MaxRequestsPerChild: maximum number of requests a server process serves
<IfModule mpm_worker_module>
    StartServers          2
    MaxClients          150
    MinSpareThreads      25
    MaxSpareThreads      75 
    ThreadsPerChild      25
    MaxRequestsPerChild   0
</IfModule>

# These need to be set in /etc/apache2/envvars
User ${APACHE_RUN_USER}
Group ${APACHE_RUN_GROUP}

#
# AccessFileName: The name of the file to look for in each directory
# for additional configuration directives.  See also the AllowOverride
# directive.
#

AccessFileName .htaccess

#
# The following lines prevent .htaccess and .htpasswd files from being 
# viewed by Web clients. 
#
<Files ~ "^\.ht">
    Order allow,deny
    Deny from all
</Files>

#
# DefaultType is the default MIME type the server will use for a document
# if it cannot otherwise determine one, such as from filename extensions.
# If your server contains mostly text or HTML documents, "text/plain" is
# a good value.  If most of your content is binary, such as applications
# or images, you may want to use "application/octet-stream" instead to
# keep browsers from trying to display binary files as though they are
# text.
#
DefaultType text/plain


#
# HostnameLookups: Log the names of clients or just their IP addresses
# e.g., www.apache.org (on) or 204.62.129.132 (off).
# The default is off because it'd be overall better for the net if people
# had to knowingly turn this feature on, since enabling it means that
# each client request will result in AT LEAST one lookup request to the
# nameserver.
#
HostnameLookups Off

# ErrorLog: The location of the error log file.
# If you do not specify an ErrorLog directive within a <VirtualHost>
# container, error messages relating to that virtual host will be
# logged here.  If you *do* define an error logfile for a <VirtualHost>
# container, that host's errors will be logged there and not here.
#
ErrorLog /var/log/apache2/error.log

#
# LogLevel: Control the number of messages logged to the error_log.
# Possible values include: debug, info, notice, warn, error, crit,
# alert, emerg.
#
LogLevel warn

# Include module configuration:
Include /etc/apache2/mods-enabled/*.load
Include /etc/apache2/mods-enabled/*.conf

# Include all the user configurations:
Include /etc/apache2/httpd.conf

# Include ports listing
Include /etc/apache2/ports.conf

#
# The following directives define some format nicknames for use with
# a CustomLog directive (see below).
# If you are behind a reverse proxy, you might want to change %h into %{X-Forwarded-For}i
#
LogFormat "%h %l %u %t \"%r\" %>s %b \"%{Referer}i\" \"%{User-Agent}i\"" combined
LogFormat "%h %l %u %t \"%r\" %>s %b" common
LogFormat "%{Referer}i -> %U" referer
LogFormat "%{User-agent}i" agent

#
# ServerTokens
# This directive configures what you return as the Server HTTP response
# Header. The default is 'Full' which sends information about the OS-Type
# and compiled in modules.
# Set to one of:  Full | OS | Minor | Minimal | Major | Prod
# where Full conveys the most information, and Prod the least.
#
ServerTokens Full

#
# Optionally add a line containing the server version and virtual host
# name to server-generated pages (internal error documents, FTP directory 
# listings, mod_status and mod_info output etc., but not CGI generated 
# documents or custom error documents).
# Set to "EMail" to also include a mailto: link to the ServerAdmin.
# Set to one of:  On | Off | EMail
#
ServerSignature On



#
# Customizable error responses come in three flavors:
# 1) plain text 2) local redirects 3) external redirects
#
# Some examples:
ErrorDocument 500 "FAIL."
#ErrorDocument 404 /missing.html
#ErrorDocument 404 "/cgi-bin/missing_handler.pl"
#ErrorDocument 402 http://www.example.com/subscription_info.html
#

#
# Putting this all together, we can internationalize error responses.
#
# We use Alias to redirect any /error/HTTP_<error>.html.var response to
# our collection of by-error message multi-language collections.  We use 
# includes to substitute the appropriate text.
#
# You can modify the messages' appearance without changing any of the
# default HTTP_<error>.html.var files by adding the line:
#
#   Alias /error/include/ "/your/include/path/"
#
# which allows you to create your own set of files by starting with the
# /usr/share/apache2/error/include/ files and copying them to /your/include/path/, 
# even on a per-VirtualHost basis.  The default include files will display
# your Apache version number and your ServerAdmin email address regardless
# of the setting of ServerSignature.
#
# The internationalized error documents require mod_alias, mod_include
# and mod_negotiation.  To activate them, uncomment the following 30 lines.

#    Alias /error/ "/usr/share/apache2/error/"
#
#    <Directory "/usr/share/apache2/error">
#        AllowOverride None
#        Options IncludesNoExec
#        AddOutputFilter Includes html
#        AddHandler type-map var
#        Order allow,deny
#        Allow from all
#        LanguagePriority en cs de es fr it nl sv pt-br ro
#        ForceLanguagePriority Prefer Fallback
#    </Directory>
#
#    ErrorDocument 400 /error/HTTP_BAD_REQUEST.html.var
#    ErrorDocument 401 /error/HTTP_UNAUTHORIZED.html.var
#    ErrorDocument 403 /error/HTTP_FORBIDDEN.html.var
#    ErrorDocument 404 /error/HTTP_NOT_FOUND.html.var
#    ErrorDocument 405 /error/HTTP_METHOD_NOT_ALLOWED.html.var
#    ErrorDocument 408 /error/HTTP_REQUEST_TIME_OUT.html.var
#    ErrorDocument 410 /error/HTTP_GONE.html.var
#    ErrorDocument 411 /error/HTTP_LENGTH_REQUIRED.html.var
#    ErrorDocument 412 /error/HTTP_PRECONDITION_FAILED.html.var
#    ErrorDocument 413 /error/HTTP_REQUEST_ENTITY_TOO_LARGE.html.var
#    ErrorDocument 414 /error/HTTP_REQUEST_URI_TOO_LARGE.html.var
#    ErrorDocument 415 /error/HTTP_UNSUPPORTED_MEDIA_TYPE.html.var
#    ErrorDocument 500 /error/HTTP_INTERNAL_SERVER_ERROR.html.var
#    ErrorDocument 501 /error/HTTP_NOT_IMPLEMENTED.html.var
#    ErrorDocument 502 /error/HTTP_BAD_GATEWAY.html.var
#    ErrorDocument 503 /error/HTTP_SERVICE_UNAVAILABLE.html.var
#    ErrorDocument 506 /error/HTTP_VARIANT_ALSO_VARIES.html.var



# Include of directories ignores editors' and dpkg's backup files,
# see README.Debian for details.

# Include generic snippets of statements
Include /etc/apache2/conf.d/

# Include the virtual host configurations:
Include /etc/apache2/sites-enabled/
```

So I am pretty much wondering...
How can I log onto root?
How can I get apache to work properly?
What am I doing wrong?

---

### Post by Joeb454 on 2008-04-08
To log into root: Open a terminal and run ```
sudo -i
```

To edit your apache.conf: ```
gksudo gedit /etc/apache2/apache2.conf
```

---

### Post by dokdoom on 2008-04-08
What other conf files are in /etc/apache2 ?

---

### Post by ibutho on 2008-04-08
Have you tried using sudo e.g. "sudo nano /etc/apache2/apache2.conf". How did you enable the root account (its locked by default hence you have to use sudo if you are an admin). As far as I can tell, Apache is working correctly but you probably need to change the server name in order for you not to see the error message printed in your post everytime you run apache.

---

### Post by jcwmoore on 2008-04-08
I am not understanding what you are trying to do here... based on that output apache is setting itself as a local web host.  if you go to your web browser and type in [http://localhost](http://localhost) (or ip address 127.0.1.1), and you see something then apache is working.  Are you trying to set up a public web page? a local web server?  I don't think the problem is with you or apache but I need to know what you are trying to do before I  can give you any meaningful advice.

---

### Post by Joeb454 on 2008-04-08
**dokdoom**, open a terminal and type (or copy) ```
ls *.conf /etc/apache2/
```

It'll list all files that end in .conf in the apache2 folder :)

---

### Post by Daelakk on 2008-04-08
Sorry, I could've given a little more information
- It's supposed to be a public web page.

I shall try the commands for editing the conf file. - Thanks (I am very new to linux... I am used to Windows >_<)
dokdoom: there is apache2.conf, envvars, httpd.conf (which is blank), and ports.conf.

Then there's the folders conf.d, mods-available, mods-enabled, sites-available and sites-enabled

---

### Post by stmiller on 2008-04-08
Also post your /etc/hosts file here.

---

### Post by Daelakk on 2008-04-08
> **stmiller said:**
> Also post your /etc/hosts file here.

```
127.0.0.1	localhost
127.0.1.1	SHELL

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

---

### Post by jcwmoore on 2008-04-08
> 
127.0.0.1       localhost
127.0.1.1       cassy.gateway.2wire.net cassy

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts


that's my /etc/hosts file.  cassy is the name of my server (hosting a public website) and that other junk is from my ISP.  sense you don't have that, (it sounds way to simple) but is everything connected properly?  you machine connected to the network? can you ping the outside world?
```
ping -c 5 google.com
```

also if you want to host a public web site you need to consider these two things...
do you have a static or dynamic IP address,  most ISP give you a dynamic IP address, see here for help setting up a dynamic IP address web site [https://help.ubuntu.com/community/DynamicDNS]("https://help.ubuntu.com/community/DynamicDNS")

if you are behind a router then you need to allow port forwarding so that you machine incomming http requests do a google search for "port forwarding (model of you router here)" and you should get enough info to figure everything out.

---

### Post by Daelakk on 2008-04-08
> **jcwmoore said:**
> that's my /etc/hosts file.  cassy is the name of my server (hosting a public website) and that other junk is from my ISP.  sense you don't have that, (it sounds way to simple) but is everything connected properly?  you machine connected to the network? can you ping the outside world?
```
ping -c 5 google.com
```

also if you want to host a public web site you need to consider these two things...
do you have a static or dynamic IP address,  most ISP give you a dynamic IP address, see here for help setting up a dynamic IP address web site [https://help.ubuntu.com/community/DynamicDNS]("https://help.ubuntu.com/community/DynamicDNS")

if you are behind a router then you need to allow port forwarding so that you machine incomming http requests do a google search for "port forwarding (model of you router here)" and you should get enough info to figure everything out.

I am connected to the network- I am on these forums and i pinged google - 0% packet loss. I think i might have a static (my ip address hasn't changed in a while).
I am behind a router though- although I've had it for a while and I know how to port forward.

edit: apache works ( i can connect with 127.0.1.1) but when i try to connect to my ip (i used whatismyip.com) , it gives me my router's page instead of apache. Will this cause problems in the future or will apache sort of take over?

---

### Post by jcwmoore on 2008-04-08
> **Daelakk said:**
> edit: apache works ( i can connect with 127.0.1.1) but when i try to connect to my ip (i used whatismyip.com) , it gives me my router's page instead of apache. Will this cause problems in the future or will apache sort of take over?

i think you need to enable port forwarding on port 80 (the http default), forward those request to your local machine, the router is stopping and returning all outside port 80 requests it looks like

EDIT: also check with you ISP to verify you have a static IP address, most people don't and they cost quite a bit more than dynamic IP service

---

### Post by halitech on 2008-04-08
if you are getting your routers page when you use your external IP then your router is not forwarding correctly or you have the external admin set to use port 80 (instead of 8080 or some other port) so you will need to resolve that issue first.

---

### Post by Daelakk on 2008-04-09
Now I have to find out how to do that... normal port forwarding hasn't worked (I forwarded port 80) and I have looked through every option in my router page and I haven't found anything.
I'll work on this tomorrow as I am quite tired and want to go to bed... 
I hope it works out eventually though.
It's weird... I was running some other kind of webserver on windows (yes, i know, it was pointless... but whatever) and my router didn't do this.
I really have no idea how to change the port my router listens on, or how to get around it.
If anyone wants to check it out, I have the Linksys WRT350N wireless router.

---

### Post by Daelakk on 2008-04-09
bump.
Still haven't figured it out.

If anyone wants to fool around, I'll give one person my username and password to my router to see what the problem is.

All you can really do that's bad is disable my internet... the reset on the back of my router works pretty well.

---

### Post by Joeb454 on 2008-04-09
You made sure you forwarded it to the right PC and everything (sounds simple, you don't know the trouble I had ;))

---

### Post by Daelakk on 2008-04-09
> **Joeb454 said:**
> You made sure you forwarded it to the right PC and everything (sounds simple, you don't know the trouble I had ;))


Yeah, I added a DHCP entry into static DHCP for my ubuntu box, it's .109
then i added port 80 to the "port forward" page (portforward.com says it's where i put it... so im not going crazy) and put it on "both tcp and udp" and put .109, then i check the box that says Enabled

---

### Post by spiderbatdad on 2008-04-09
In a terminal window enter```
sudo a2ensite default
sudo apache2ctl stop
sudo apache2ctl start
```

If there are no config errors the sever will start.
Open your web browser and type 127.0.0.1 in the address bar.
You should see the it works page.

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

[https://help.ubuntu.com/7.10/server/C/httpd.html#https-configuration](https://help.ubuntu.com/7.10/server/C/httpd.html#https-configuration)

---

### Post by Daelakk on 2008-04-10
> **spiderbatdad said:**
> In a terminal window enter```
sudo a2ensite default
sudo apache2ctl stop
sudo apache2ctl start
```

If there are no config errors the sever will start.
Open your web browser and type 127.0.0.1 in the address bar.
You should see the it works page.

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

[https://help.ubuntu.com/7.10/server/C/httpd.html#https-configuration](https://help.ubuntu.com/7.10/server/C/httpd.html#https-configuration)

Yes, I have it working, that's not my problem.
It's when i try to connect from outside is what's the problem.
When I connect to my IP address, it gives me the config page for my router, so the router is blocking incoming port 80 connections, although i have port 80 forwarded.
Try going to threecheersforteamwork.ath.cx and see what you get?

---

### Post by matt79 on 2008-04-10
One or two things to look at while you are setting up your router. One just because your ip has not changed for awhile does not mean it is static. Mine changes when I shutdown my router for awhile, but stays the same if I leave it on. You can check your WAN ip by going to "canyouseeme.org". If your server works locally then it should just be a matter of configuring your router. One thing to remember is that in order to test your server from your WAN ip address you have to be on a another computer that is not in your LAN network. Try testing it from a friends computer. Another thing to check out is see if your ISP is blocking port 80. Mine does so I just run mine off of port 443. If you want you can email me your WAN ip and I can try and help.

---

### Post by spiderbatdad on 2008-04-10
> **Daelakk said:**
> Yes, I have it working, that's not my problem.
It's when i try to connect from outside is what's the problem.
When I connect to my IP address, it gives me the config page for my router, so the router is blocking incoming port 80 connections, although i have port 80 forwarded.
Try going to threecheersforteamwork.ath.cx and see what you get?

If you are getting the config page for you router, then you are connecting to the ip of the router...you need your actual ip address...Please follow this link, and try to connect to the ip it shows.
[http://www.whatismyip.org/](http://www.whatismyip.org/)

---

### Post by OffAxis on 2008-04-10
@matt79
> One thing to remember is that in order to test your server from your WAN ip address you have to be on a another computer that is not in your LAN network.

This is not true.

You **absolutely **can be within your LAN and connect successfully to your WAN IP; you can even be on the same computer.

You should be able to hit your apache server one of four ways;

1. while at your server you should be able to hit [http://localhost](http://localhost)
2. from within your LAN (can be at your server) you can hit your server's internal IP (192.168.xxx)

Those two test to see if apache is functioning. To see if your router is forwarding correctly you can:

3. from any machine (LAN or internet) hit your WAN IP.


And finally, to see if your DNS is setup or registered correctly:

4. from any machine (LAN or internet) hit your url (your website's name); eg. [http://yoursite.com](http://yoursite.com)

---

### Post by echo.whoami on 2008-04-10
If you want to log in as root you should enable the account first. go to system>administration>users and groups and in root account give a password. Then go to  system> administration>login windows and in the security tab click the box "Allow local system administrator to login". So you will be ready to login from gnome login screen as root. 

If you want to enable a site go to etc/apache2/sites-enabled/ there will be a file. Open it with a text editor change where the document root you want. the default is /var/www/. so if your files are in a folder named site copy the folder in /var/www/ and change the document root to /var/www/site.

that's worked for me. 

if you want your web server to accessible from the world you should open the ports on firewall and router. A good idea is also to get a domain. If your ip from isp is dynamic you could go to dyndns.com or no-ip.com and get a domain from them. Maybe your router supports one of this dynamic dns services and from the router interface give the  username and password of your account from the dynamic dns service that you will choose.

---

### Post by Daelakk on 2008-04-10
> **spiderbatdad said:**
> If you are getting the config page for you router, then you are connecting to the ip of the router...you need your actual ip address...Please follow this link, and try to connect to the ip it shows.
[http://www.whatismyip.org/](http://www.whatismyip.org/)

That's what I have used, and I am connecting to my actual ip address... 24.65.***.***
It still redirects to my router, because the router is blocking it even though the port is forwarded. So it is probably my ISP. 
canyouseeme.org reports that it cannot connect to anything on my ip on port 80. 
I will try a different port and use no-IP.com

edit: changed my port to 443 (or I think so)
To do that, do you put in the config...
Listen 443

or do you put 443 in the ServerName?
This always confused me...

---

### Post by matt79 on 2008-04-10
> **OffAxis said:**
> @matt79


This is not true.

You **absolutely **can be within your LAN and connect successfully to your WAN IP; you can even be on the same computer.

You should be able to hit your apache server one of four ways;

1. while at your server you should be able to hit [http://localhost](http://localhost)
2. from within your LAN (can be at your server) you can hit your server's internal IP (192.168.xxx)

Those two test to see if apache is functioning. To see if your router is forwarding correctly you can:

3. from any machine (LAN or internet) hit your WAN IP.


And finally, to see if your DNS is setup or registered correctly:

4. from any machine (LAN or internet) hit your url (your website's name); eg. [http://yoursite.com](http://yoursite.com)



An internet user inside your LAN cannot access your external public IP address and come back in; internal users should access the server on its local internal IP address, or you can set up an alias in a Windows hosts file. This also applies if you are using a URL (web address) which resolves to your public IP address - internal LAN users will not be able to use that URL - the packet is not 'bounced' back into the LAN by the forwarding rules - they apply to incoming external users only.

---

### Post by matt79 on 2008-04-10
> **Daelakk said:**
> That's what I have used, and I am connecting to my actual ip address... 24.65.***.***
It still redirects to my router, because the router is blocking it even though the port is forwarded. So it is probably my ISP. 
canyouseeme.org reports that it cannot connect to anything on my ip on port 80. 
I will try a different port and use no-IP.com

edit: changed my port to 443 (or I think so)
To do that, do you put in the config...
Listen 443

or do you put 443 in the ServerName?
This always confused me...
No you should leave that port on your server listening to 80. What you need to do is get a no-ip account. Lets say your no-ip domain name is "daelakk.hopto.org". You set daelakk.hopto.org to use port 443. Then you set your router to forward port 443 from the internet (WAN) to port 80 on your local network (LAN). So if I connect to your server I am using port 443 until I get past your ISP and to your router. Then after I go past your router I am using port 80 on your network. One problem you might be having is you have to forward in coming connections to your servers local ip address. For example: Lets say your server's local ip address is 192.168.1.10. You would say from the WAN use port 443 until you get to my router, then take incoming connections from port 443 and forward them to 192.168.1.10 on port 80 on my LAN.

---

### Post by Daelakk on 2008-04-10
So I put in my config file...
```
Listen 80
```
and it says it cannot bind to 0.0.0.0:80
```
(98)Address already in use: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs
```
(there is no httpd started.. when i tell it to stop it says it isn't running)
So I put..
```
Listen myipaddress:80
```
and it says
```
(99)Cannot assign requested address: make_sock: could not bind to address 24.65.---.---:80
no listening sockets available, shutting down
Unable to open logs
```
so I remove the Listen line altogether and it works, but I'm not sure it's even listening on that port like to the outside... but it works on internal... so if it works internal it *should* work external? if my router wasn't gay?

---

### Post by matt79 on 2008-04-10
try putting this in

Listen 80

<IfModule mod_ssl.c>
    Listen 443
</IfModule>

The file you should edit is "ports.conf"

---

### Post by Daelakk on 2008-04-10
> **matt79 said:**
> try putting this in

Listen 80

<IfModule mod_ssl.c>
    Listen 443
</IfModule>

Again I get...
```
jon@SHELL:~$ sudo apache2ctl start
(98)Address already in use: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs
```

I could give you ssh/telnet access to my computer
but oh wait... noone can connect to it from outside
>_<

---

### Post by matt79 on 2008-04-10
are you putting this info in the "ports.conf"?

---

### Post by Daelakk on 2008-04-10
> **matt79 said:**
> are you putting this info in the "ports.conf"?

yes.. i swear...
:lolflag:
ports.conf already has that..

---

### Post by matt79 on 2008-04-10
if it already has it then you do not need to add anything.
If you can access it locally with out having to put a port # after the server's ip address  it the it should be fine
You should just have to do the port forwarding in your router.

---

### Post by Daelakk on 2008-04-10
I tried listening on some obscure port and forwarded it with my router. I can connect with localhost and with my internal LAN ip but still not with my WAN ip

yeah thats the thing
my router won't port forward to save it's life
i don't know what's wrong with it...

my router page
[[IMG]http://img237.imageshack.us/img237/6817/screenshotpx8.th.png[/IMG]](http://img237.imageshack.us/my.php?image=screenshotpx8.png)

---

### Post by matt79 on 2008-04-10
> **Daelakk said:**
> I tried listening on some obscure port and forwarded it with my router. I can connect with localhost and with my internal LAN ip but still not with my WAN ip

yeah thats the thing
my router won't port forward to save it's life
i don't know what's wrong with it...

Do you know how to forward ports in your router? Sometimes it can be tricky it took me awhile to figure out how mine worked.

---

### Post by Daelakk on 2008-04-10
yes I do
check the picture in the previous post
am i doing anything wrong...?
i have set a DHCP reservation for my ubuntu computer so it's the same internal IP every time, and i put the ending of the ip in the box that's blacked out, it's the same for all of them
i dunno why i blacked it out, people do that usually so i did just in case.

---

### Post by matt79 on 2008-04-10
I must ask when you say the same do you mean that under the black it is 192.168.1.0?
 Sorry I had missed the photo in the post

---

### Post by Daelakk on 2008-04-10
> **matt79 said:**
> I must ask when you say the same do you mean that under the black it is 192.168.1.0?
 Sorry I had missed the photo in the post

under the black is the end of it
so 192.168.1.lastthreenumbers, not 0
i dunno does it even matter if i tell you what it is

---

### Post by matt79 on 2008-04-10
Not really because it is behind your router. But you do not have to as long as it ends with the same ip as your server. Meaning if your server's ip is 192.168.1.10 that last number forwards port 443 to 80 on the ip address ending in .10

---

### Post by Daelakk on 2008-04-10
yeah that's what it is.
how do i double check on ubuntu? I've set a DHCP in my router that sets the internal to my MAC address every time, but id like to double check on the OS itself.

---

### Post by matt79 on 2008-04-10
ifconfig

---

### Post by matt79 on 2008-04-10
But I am looking at your photo that you sent me and it looks like you are forwarding the same WAN port to the same LAN port. i.e. 80 to 80.
You need to go 443 to 80.

---

### Post by Daelakk on 2008-04-10
confirmed that the ip im "forwarding" to is the same as my server
what the hell...

---

### Post by matt79 on 2008-04-10
Take port 443 forward it to 80 then set the ip that you forward it to the same as your server's ip

---

### Post by matt79 on 2008-04-10
I got to go for a bit be back later.

---

### Post by matt79 on 2008-04-10
ok try and make your router look like this photo. Only change the 10 to the last digit of your server's ip.
[[IMG]http://img247.imageshack.us/img247/7721/screenshotpx8le6.th.png[/IMG]](http://img247.imageshack.us/my.php?image=screenshotpx8le6.png) Then go to canyouseeme.org and try port 443 and port 22.

---

### Post by Daelakk on 2008-04-11
Set it up exactly like the picture; canyouseeme.org cannot see the service on my IP (connection timed out)
my router is really starting to make me mad
first it kills my internet every two weeks or so and i have to reset it
and now it won't forward my ports.
great.
and it's fairly new too- only about 5 months old. top of the line router.
Shitty.

Read some other things on the linksys forums, seems alot of people are having problems with this router. Maybe I should've done some research before purchasing...
Anyway I might try what one of the people suggested; taking the covers off and blowing a fan on the components.. it seems they get pretty hot. Probably won't help the port forward problem, but it would help the internet not dying every few days. Port forward is probably a firmware issue that linksys probably won't resolve anytime soon, seeing as the firmware on the site was last updated in 2006...

---

### Post by Daelakk on 2008-04-11
SOLVED.
I updated to a dd-wrt firmware (not official) and port forwarding ACTUALLY WORKS!
All problems solved-
Thanks matt79 for all your help- it's REALLY appreciated!
I owe you one.

---

### Post by apostate on 2008-04-11
> **matt79 said:**
> An internet user inside your LAN cannot access your external public IP address and come back in; internal users should access the server on its local internal IP address, or you can set up an alias in a Windows hosts file. This also applies if you are using a URL (web address) which resolves to your public IP address - internal LAN users will not be able to use that URL - the packet is not 'bounced' back into the LAN by the forwarding rules - they apply to incoming external users only.

This is correct. The IP of his router is the only public IP he has, his machine  has only a private IP which is provided *by the router* via NAT.   This is why port forwarding becomes an issue in the first place.  Very few residential DSL gateways have the option of changing the port for the admin page, they simply route port 80 requests that are from within the network perimeter to the admin page, and port 80 requests that are from outside to...nowhere.  Unless you have set up port forwarding, in which case outside requests will go to his server, but he isn't outside when he tries to hit his own server from the server itself, or the other home PCs.  Port forwarding may be working correctly, but he still isn't going to see his web-page by browsing to his public IP from within his own LAN. It *will NOT work*. 

He would need to test from a friends PC, or from work. This is a limitation of the residential gategay, which is not a full-featured router.

---

### Post by Daelakk on 2008-04-11
> **apostate said:**
> This is correct. The IP of his router is the only public IP he has, his machine  has only a private IP which is provided *by the router* via NAT.   This is why port forwarding becomes an issue in the first place.  Very few residential DSL gateways have the option of changing the port for the admin page, they simply route port 80 requests that are from within the network perimeter to the admin page, and port 80 requests that are from outside to...nowhere.  Unless you have set up port forwarding, in which case outside requests will go to his server, but he isn't outside when he tries to hit his own server from the server itself, or the other home PCs.  Port forwarding may be working correctly, but he still isn't going to see his web-page by browsing to his public IP from within his own LAN. It *will NOT work*. 

He would need to test from a friends PC, or from work. This is a limitation of the residential gategay, which is not a full-featured router.

Actually I *can* access my outside IP from the internal... I just went to my IP address on port 80 and it gave me the **It works!** page... so it works. I just had to get a different firmware from the official Linksys one and port forwarding finally worked. Linksys didn't do very much quality control or testing on this product... it seems like it was rushed to the market to make a bigger profit. Big mistake- lots of people are buying different brands now. I bought into the hype- I'm not gonna lie. Thanks god for third-party solutions.

---

### Post by matt79 on 2008-04-11
> **Daelakk said:**
> Actually I *can* access my outside IP from the internal... I just went to my IP address on port 80 and it gave me the **It works!** page... so it works. I just had to get a different firmware from the official Linksys one and port forwarding finally worked. Linksys didn't do very much quality control or testing on this product... it seems like it was rushed to the market to make a bigger profit. Big mistake- lots of people are buying different brands now. I bought into the hype- I'm not gonna lie. Thanks god for third-party solutions.
Well I am guessing that there are different ways to set up your server. Maybe certain routers are able to do the loopback feature to a WAN ip from the LAN automatically. But if you have it working on the WAN thats what counts:guitar:

---

### Post by OffAxis on 2008-04-15
> Maybe certain routers are able to do the loopback feature to a WAN ip from the LAN automatically
?
No.
The request still goes external and then comes back to the WAN IP.

Any router that has port forwarding enabled should function this way; the WAN IP gets a request on port 80 and forwards it through.

You can verify this by unplugging your internet cable and try connecting to your router's former WAN IP.
(From the server) http:.//localhost, (from the LAN) 192.16.x.x should still work, but from anywhere the WAN address should fail.

---

### Post by matt79 on 2008-04-18
> **OffAxis said:**
> ?
No.
The request still goes external and then comes back to the WAN IP.

Any router that has port forwarding enabled should function this way; the WAN IP gets a request on port 80 and forwards it through.

You can verify this by unplugging your internet cable and try connecting to your router's former WAN IP.
(From the server) http:.//localhost, (from the LAN) 192.16.x.x should still work, but from anywhere the WAN address should fail.

We are talking about accessing your server from you LAN network using your WAN ip. For example if my local network is 192.168.1.0 and my WAN ip address is 70.168.6.200. I am sayijng that sometimes that you can not access your server using 70.168.6.200 from your LAN network 192.168.1.0.

---


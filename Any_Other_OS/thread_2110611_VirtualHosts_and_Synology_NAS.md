---
title: "VirtualHosts and Synology NAS"
date: 2013-01-30
forum: Any Other OS
---

### Post by TooNick on 2013-01-30
Hi, I'm trying to setup a reverse proxy to point my webaddress to different home servers or ports. So what I'm basically trying to do is
name.dyndns-ip.com --> website on localhost
adm.name.dyndns-ip.com --> port ... on localhost
subsonic.name.dyndns-ip.com --> port ... on other internal ip
camera.name.dyndns-ip.com --> other internal ip
I edited the httpd-vhost.conf-user like this:
> 
LoadModule proxy_module modules/mod_proxy.so
LoadModule proxy_http_module modules/mod_proxy_http.so
LoadModule proxy_connect_module modules/mod_proxy_connect.so
NameVirtualHost *:80

<VirtualHost *:80>
ServerName name.dyndns-ip.com
ServerAlias name.dyndns-ip.com
ProxyRequests Off
ProxyVia Off
<Proxy *>
 Order deny,allow
 Allow from all
</Proxy>
ProxyPass / [http://internal:4040/](http://internal:4040/)
ProxyPassReverse / [http://internal:4040/](http://internal:4040/)
</VirtualHost>
<VirtualHost *:80>
ServerName adm.name.dyndns-ip.com
ServerAlias adm.name.dyndns-ip.com
ProxyRequests Off
ProxyVia Off
<Proxy *>
 Order deny,allow
 Allow from all
</Proxy>
ProxyPass [http://internal:5000/](http://internal:5000/)
ProxyPassReverse [http://internal:5000/](http://internal:5000/)
</VirtualHost>I can connect to name.dyndns-ip.com which points me to the internal:4040 correctly. However I can't connect to adm.name.dyndns-ip.com Does anyone know how to get this to work? I didn't edit any other config files.

---

### Post by volkswagner on 2013-01-30
What happens when you try to navigate to adm.name.dyndns-ip.com?

I suggest creating individual vhost files for each servername.  This can make diagnosing and maintenance easier.  With individual vhost files you can enable and disable on site at a time.

For sites on the same machine you should use localhost, like:

```
ProxyPass http://localhost:5000/
ProxyPassReverse http://localhost:5000/
```

You should not need to duplicate servername and serveralias when they are equal.

One other setting which can help when forwarding to another machine is to perserve the url with:

```
ServerName yoursever
Serveralias www.yourserver
[COLOR="Navy"]ProxyPreserveHost on[/COLOR]

```


I suggest you move:

```
NameVirtualHost *:80
```

to /etc/apache2/ports.conf

Also you should not need the following in your vhost file.  These are global mods loaded once with "sudo a2enmod proxy" or similar.
```
LoadModule proxy_module modules/mod_proxy.so
LoadModule proxy_http_module modules/mod_proxy_http.so
LoadModule proxy_connect_module modules/mod_proxy_connect.so
```

---

### Post by TooNick on 2013-01-31
The error I get when I navigate is: Server not found. The same error I would get if I just typed in random stuff. I changed the internal:5000 to localhost:5000 but no succes :( I can get one of the 2 to work, but not both. For instance if I remove the adm. at localhost:5000 it works, but then I have to remove the internal:4040 port forward...
EDIT: adding preservehost to the script doesn't change anything either. My script is now:
> LoadModule proxy_module modules/mod_proxy.so
LoadModule proxy_http_module modules/mod_proxy_http.so
LoadModule proxy_connect_module modules/mod_proxy_connect.so
NameVirtualHost *:80

<VirtualHost *:80>
ServerName name.dyndns-ip.com
ServerAlias name.dyndns-ip.com
ProxyPreserveHost On
ProxyRequests Off
ProxyVia Off
<Proxy *>
 Order deny,allow
 Allow from all
</Proxy>
ProxyPass / [http://internal:4040/]("http://192.168.178.11:4040/")
ProxyPassReverse / [http://internal:4040/]("http://192.168.178.11:4040/")
</VirtualHost>

<VirtualHost *:80>
ServerName name.dyndns-ip.com
ServerAlias [www.name.dyndns-ip.com]("http://www.name.leenders.dyndns-ip.com")
ProxyPreserveHost On
ProxyRequests Off
ProxyVia Off
<Proxy *>
 Order deny,allow
 Allow from all
</Proxy>
ProxyPass / [http://localhost:5000/](http://localhost:5000/)
ProxyPassReverse / [http://localhost:5000/](http://localhost:5000/)
</VirtualHost>
I couldn't find the ports.conf, I'm using a synology which doesn't use ubuntu. Sorry for using this forum for it but I couldn't get any help elsewhere.

---

### Post by sandyd on 2013-01-31
moved to other os talk

---

### Post by volkswagner on 2013-02-08
Have you tried moving your hosts to individual files?

Here is an example of my vhost file.  This does not change the port but adding the port should not affect the function.

I also have in /etc/apache2/mods-enabled:
proxy.conf
proxy_http.load
proxy.load




```
<VirtualHost *>
        ServerAdmin eric@domain.com
        ServerName server2.domain.com
        ServerAlias www.server2.domain.com
        ProxyPreserveHost on
         <location />
          allow from all
     </location>


        ProxyPass / http://192.168.7.61/
        ProxyPassReverse / http://192.168.7.61/

</VirtualHost>

```

This works for Apache2 passing to IIS and other apache2 servers on the LAN.

I suggest trying individual vhost files.

---

### Post by TooNick on 2013-02-09
Thanks for your reply, I tried your code but didn't work. The problem might be tht I apperently have 2 modems ( i didn't know before, because I am not the owner of the modems...). However I did get it to work using ip.com/subsonic/ and ip.com/synology but now I can't login via browsers, but via apps is works fine though...

---


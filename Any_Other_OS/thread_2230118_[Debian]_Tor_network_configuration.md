---
title: "[Debian] Tor network configuration"
date: 2014-06-17
forum: Any Other OS
---

### Post by zooobie on 2014-06-17
Hi

I am running on Debian 7.5 64 bits under Gnome interface and I would like to use the tor network when I browse on the internet with Google Chrome Browser. 
I installed tor and privoxy :
```
 [COLOR=#111111][FONT=Consolas]apt-get install tor privoxy[/FONT][/COLOR]
```
I added the line
> [COLOR=#111111][FONT=Consolas]forward-socks4a   /               127.0.0.1:9050 .[/FONT][/COLOR] 
to the privoxy configuration's file.
Here you are this latter file :

```
# Generally, this file goes in /etc/privoxy/config
forward-socks4a / 127.0.0.1:9050 .
confdir /etc/privoxy
logdir /var/log/privoxy
actionsfile standard
actionsfile default
actionsfile user
filterfile default.filter
 
debug   4096
debug   8192
 
user-manual /usr/share/doc/privoxy/user-manual
listen-address  127.0.0.1:8118
toggle  1
enable-remote-toggle 0
enable-edit-actions 0
enable-remote-http-toggle 0
buffer-limit 4096

```I launched the privoxy and tor's services :
```
[COLOR=#111111][FONT=Consolas]/etc/init.d/privoxy start[/FONT][/COLOR] 
[COLOR=#111111][FONT=Consolas]/etc/init.d/tor start[/FONT][/COLOR] 
```

The circuit was successfully built.

Then I launched Chrome (NOT in ROOT) with the following manual proxy settings :
HTTP proxy : 127.0.0.1 to the port 8118

However, when I go to the page : [https://check.torproject.org/](https://check.torproject.org/)

it says that I am not using Tor.

Can you help me to configure tor on lmy computer ?

Thanks

---

### Post by bapoumba on 2014-06-17
*Thread moved to **Other OS/Distro Support**.*

---

### Post by Nobody Nessie on 2014-06-18
Forward socks5, port 9150 ?

---


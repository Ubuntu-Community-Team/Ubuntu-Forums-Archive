---
title: "Dynamic DNS ubuntu breezy PROBLEMS!!!!"
date: 2006-07-13
forum: Absolute Beginner Talk
---

### Post by botcolon on 2006-07-13
I have tried setting a dyndns domain and have it point to my ubuntu server with no success. My linux server updates its local ip address(e.g 192.168.17.2) to dyndns.org. (this is with ez-ipupdate)

Can someone suggest or indicate where I am going wrong here or a better alternative than ez-ipupdate? ipcheck didn't work for me either, something about deleting a ipcheck.dat file?????

my setup is

-cable modem->linksys router(192.168.17.1)with port Upnp 80ext-81int--->ubuntu 192.168.17.2:81

also can someone clear up if my hostname of my linux box must match the domain I choose from dyndns? if so, what other files will need to be changed (e.g apache2, mysql, php5, gallery2????)

any help would be great. I am pulling my hair out.

michael

---

### Post by botcolon on 2006-07-13
has anyone experienced this issue?

---

### Post by botcolon on 2006-07-15
bump

---

### Post by Daniel15 on 2006-07-15
I too would like to know about this, as all the scripts I tried kept updating using my local IP address. At the moment, I need to log in to the DynDNS website to update the entry, which is a bit of a pain...

> also can someone clear up if my hostname of my linux box must match the domain I choose from dyndns? if so, what other files will need to be changed (e.g apache2, mysql, php5, gallery2????)
No, not at all. My Linux box has a hostname of 'server1.dan-network.local' and it still works as expected ;)

---

### Post by [S|G] on 2006-07-15
This is happening because it is sending its internal network IP number. Can you post the update script configuration here? An easy way to work around this is using an web-based IP check.

I use dyndns but I'm not currently running any automatic update client. However, take a look at this page: [https://www.dyndns.com/support/clients/unix.html](https://www.dyndns.com/support/clients/unix.html)

They also have a configuration walkthrough for ddclient here: [https://www.dyndns.com/support/kb/archives/using_ddclient_with_dyndns_services.html](https://www.dyndns.com/support/kb/archives/using_ddclient_with_dyndns_services.html)

EDIT: The important part of the configuration that will fix your problems is:
```

## via our CheckIP server
#use=web, web=checkip.dyndns.org/, web-skip='IP Address'

```

You should uncomment those lines. That will make the client use your internet IP instead of your network IP since it'll be checked at an external server.

---

### Post by Daniel15 on 2006-07-15
Yep, it's fixed now. I reintalled ddclient, and it's working perfectly... Thanks!

---

### Post by botcolon on 2006-07-15
yep. fixed. thanks

---


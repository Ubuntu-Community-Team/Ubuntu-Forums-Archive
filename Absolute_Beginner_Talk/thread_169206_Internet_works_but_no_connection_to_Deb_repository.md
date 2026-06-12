---
title: "Internet works but no connection to Deb repository"
date: 2006-05-02
forum: Absolute Beginner Talk
---

### Post by richag77 on 2006-05-02
I have an internet connection through Firefox, that's fine, but cannot as yet get a connection through Synaptic or via a terminal(root or otherwise). "apt-get update" just times out.

I'm a newbie and would like to get a few pointers about where to start going to solve this one. After this, and sorting out email via Evolution I'm migrating to Ubuntu from XP. Hope that's enuff info.   Bye

Hi souki,
            /etc/resolv.conf   is
nameserver 192.168.1.1
domain smartaflow.com

---

### Post by souki on 2006-05-02
can you post your /etc/resolv.conf ?

---

### Post by ESPOiG on 2006-05-02
i had the same problem it ended up being that my ISP (AMCOM) hadnt given me the DNS Servers that i needed, once i had them it work fine

edit them at System>Administration>Network Settings>DNS

or /etc/resolv.conf

just make sure if you do it via nano/gedit/text editor put them like so >
nameserver xxx.xxx.xxx.xxx
nameserver xxx.xxx.xxx.xxx

hope this helps, ESPOiG

just email your ISP for them :D

#EDITED

lol beaten :D

---

### Post by geek.de.nz on 2006-05-02
Try to ping google in a console
```
ping google.com
``` 
If that doesn't work, try to ping google with just the ip:
```
ping 72.14.207.99
``` 
If the last one works but the one before not, your DNS is probably not working properly. Try
```

sudo dhclient
``` 
If that doesn't work or you have setup your ip statically, put your DNS server IPs in /etc/resolv.conf
```

sudo pico /etc/resolv.conf
#add the line(s)
nameserver xxx.xxx.xxx.xxx #your DNS server IP here

``` 
Hope that helps.

---


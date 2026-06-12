---
title: "Problems with Synaptic"
date: 2008-02-10
forum: Absolute Beginner Talk
---

### Post by Djalmahal on 2008-02-10
Hi,

so, yesterday I checked out the Tor program and JAP which let you modify proxy settings, i was curious. Now today, I can still run Firefox and all, but when I want to install a program with Synaptic or Add/Remove Programs it gives me this line

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/f/freedoom/freedoom_0.5-1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/f/freedoom/freedoom_0.5-1_all.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/p/prboom/prboom_2.4.6+dfsg-1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/p/prboom/prboom_2.4.6+dfsg-1_i386.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)


As i said, Firefox is fine, as far as I'm aware tor or jap is not running, i'm not using a proxy, so any ideas what;s up?

Thanks
Andreas

---

### Post by zipperback on 2008-02-10
Launch Synaptic...

System -> Administration -> Synaptic Package Manager

The check your synaptic network connection settings.

Settings -> Preferences

Now click the Network tab.

Adjust your network connectivity for synaptic as needed.

- zipperback
:popcorn:

---

### Post by spiderbatdad on 2008-02-10
TOR uses anon-proxy which may continue to be used in /sbin. This demon service screws up a lot of users. Good luck. you may need to purge TOR and anon-proxy then use ```
HTTP_PROXY=
http_proxy=
``` also diable all proxies in network. Localhost 4001 is the default for anon-proxy

---

### Post by spiderbatdad on 2008-02-10
```
sudo apt-get remove --purge anon-proxy
```

---

### Post by Djalmahal on 2008-02-10
Ok, 

thanks purging tor was enough, i guess that my system is back to its original state, once again, ubuntuforums is great, took 20min to get a valuable answers to my question, thanks

ANdreas

---


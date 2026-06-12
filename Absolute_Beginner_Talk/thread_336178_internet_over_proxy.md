---
title: "internet over proxy"
date: 2007-01-11
forum: Absolute Beginner Talk
---

### Post by timon_tg on 2007-01-11
Hi,
Can anyone help me to config my ubuntu PC, so I could work with wget and apt-get in console.
The ISP use proxy with Authorization and no ping is allowed over the proxy.
10x

---

### Post by JDahl on 2007-01-11
apt should work automatically via your http proxy if you setup the environment variable
to something like:

export http_proxy=http://<proxy_ur>:<proxy_port>

---

### Post by timon_tg on 2007-01-11
Yes , I set up http_proxy in /etc/bash.bashrc and apt-get and wget is working now! 10x

The second thing I want to manage is the way that firefox ask me everythime for user and pass, because of the proxy authorization.
Is there a way to use squid or something else in which to set up my main proxy as a parent proxy and then to config proxy setting globaly for the system, so I don't have to enter proxy setings for every application accessing internet?
10x

---

### Post by jonathan.lees on 2007-01-11
You can configure Squid for an upstream proxy. Open your squid.conf file and in the section Options which affect the neighbor selection at the end of it type the following line:

```

cache_peer proxy parent 8080 0 no-query default login=Username:Password

```

Where proxy is your ISP proxy, 8080 their port and your Username:Password

---


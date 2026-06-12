---
title: "tor not working"
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by ninjad on 2007-05-14
I tried installing tor using the .deb package from the tor.eff.org page but that didnt work, so i tried using apt-get. I  followed satellite360's instructions and did everything he said but i still get this error when i try to run tor or privoxy through terminal.

```

Starting filtering proxy server: privoxy.

Setting up tor (0.1.1.26-1) ...
debian-tor uid check: ok
debian-tor homedir check: ok
Raising maximum number of filedescriptors (ulimit -n) to 8192.
Starting tor daemon: tor...
May 14 20:34:48.478 [notice] Tor v0.1.1.26. This is experimental software. Do not rely on it for strong anonymity.
May 14 20:34:48.480 [notice] Initialized libevent version 1.1a using method epoll. Good.
May 14 20:34:48.481 [warn] /var/lib/tor is not owned by this user (debian-tor, 115) but by ninjad (1000). Perhaps you are running Tor as the wrong user?
May 14 20:34:48.481 [warn] Failed to parse/validate config: Couldn't access/create private data directory "/var/lib/tor"
May 14 20:34:48.481 [err] tor_init(): Reading config failed--see warnings above. For usage, try -h.
invoke-rc.d: initscript tor, action "start" failed.
dpkg: error processing tor (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 tor
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Any ideas why tor can't create its own directory?

Thanks

---

### Post by Cypher on 2007-05-15
Open up a terminal by going to Applications->Accessories->Terminal and type
```

ls -l /var/lib
cat /etc/passwd

```
and show us the results..

---

### Post by Dr Small on 2007-05-15
I posted a fix for this back at here:
[http://ubuntuforums.org/showthread.php?p=2637580#post2637580](http://ubuntuforums.org/showthread.php?p=2637580#post2637580)

Just download the shell script, run it, and it should install tor for you ;)
[http://ubuntuforums.org/attachment.php?attachmentid=32360&d=1178918902](http://ubuntuforums.org/attachment.php?attachmentid=32360&d=1178918902)

Dr Small

---


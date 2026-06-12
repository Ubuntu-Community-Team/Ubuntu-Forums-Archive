---
title: "Wordpress installation problem"
date: 2013-01-09
forum: Any Other OS
---

### Post by satimis on 2013-01-09
Hi all,

Ubuntu 12.04 desktop 64bit

I followed;

1)
How To Install LAMP Server in Ubuntu Server 12.04 LTS
[http://ubuntuserverguide.com/2012/05/how-to-install-lamp-server-in-ubuntu-server-12-04-lts.html](http://ubuntuserverguide.com/2012/05/how-to-install-lamp-server-in-ubuntu-server-12-04-lts.html)

2)
How to install WordPress in Ubuntu Server 12.04 LTS Precise Pangolin
[http://ubuntuserverguide.com/2012/05/how-to-install-latest-wordpress-in-ubuntu-server-12-04-lts.html](http://ubuntuserverguide.com/2012/05/how-to-install-latest-wordpress-in-ubuntu-server-12-04-lts.html)

On running;
$ sudo bash /usr/share/doc/wordpress/examples/setup-mysql -n wordpress_preciseserver blog.preciseserver.com
ping: unknown host blog.preciseserver.com

Please advise how to fix this problem? TIA

Regards
satimis

---

### Post by dannyboy79 on 2013-01-09
that step you're trying is only If you have installed virtual host on server and/or already know your URL.

Have you gotten a FQDN yet? From a service like dyndns?

---

### Post by Habitual on 2013-01-09
> **dannyboy79 said:**
> that step you're trying is only If you have installed virtual host on server and/or already know your URL.

Have you gotten a FQDN yet? From a service like dyndns?

127.0.0.1 <tab>blog.preciseserver.com in /etc/hosts should work.
I've used this method before successfully, but not with a sub-domain.

YMMV

---

### Post by satimis on 2013-01-09
> **dannyboy79 said:**
> that step you're trying is only If you have installed virtual host on server and/or already know your URL.
Whether on;
```

$ sudo bash /usr/share/doc/wordpress/examples/setup-mysql -n wordpress_preciseserver blog.preciseserver.com
```
replacing "blog.preicseserver.com" with my url "www.abc.com"?  Thanks

> 
Have you gotten a FQDN yet? From a service like dyndns?
Yes, I have domains registered with godaddy.

B.R.
satimis

---

### Post by satimis on 2013-01-09
> **Habitual said:**
> 127.0.0.1 <tab>blog.preciseserver.com in /etc/hosts should work.
I've used this method before successfully, but not with a sub-domain.

Hi, 

$ cat /etc/hosts```

127.0.0.1       localhost
127.0.1.1       localhost.localdomain   localhost

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
satimis@localhost:~$ 

```
Whether replacing "localhost" with "blog.preciseserver.com" on following line```

127.0.0.1       localhost

```
?

Thanks

I found following thread;

WordPress
[https://help.ubuntu.com/community/WordPress](https://help.ubuntu.com/community/WordPress)

I'm not very clear about;
Enable the Universe repository
1) I am using Ubuntu server (command line)
2) I am using a desktop
???

I'm now working on Ubuntu desktop and have LAMP installed already.


Regards
satimis

---


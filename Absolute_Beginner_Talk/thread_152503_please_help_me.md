---
title: "please help me"
date: 2006-03-30
forum: Absolute Beginner Talk
---

### Post by 5jarinko on 2006-03-30
I can not use sudo apt-get update

I have to use prosy server

but if I put to file /etc/apt/apt.conf information about my proxy it is does not work

example:


root@hasox:/etc/apt# cat /etc/apt/apt.conf
APT::Authentication::TrustCDROM "true";
Acquire::http::Proxy "http://logi:my_password@ip_adress_of_proxy:8080";
Acquire::::Proxy "false";

---

### Post by nanotube on 2006-03-30
[QUOTE=5jarinko]I can not use sudo apt-get update

I have to use prosy server

but if I put to file /etc/apt/apt.conf information about my proxy it is does not work

example:


root@hasox:/etc/apt# cat /etc/apt/apt.conf
APT::Authentication::TrustCDROM "true";
Acquire::http::Proxy "http://logi:my_password@ip_adress_of_proxy:8080";
Acquire::::Proxy "false";[/QUOTE]

try removing the last line you have in there.

---

### Post by 5jarinko on 2006-03-30
same problem,

root@hasox:/etc/apt# cat apt.conf
APT::Authentication::TrustCDROM "true";
Acquire::http::Proxy "http://*****@10.1.1.41:8080";



Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy-updates/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy-updates/universe/binary-i386/Packages.gz)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy-updates/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy-updates/multiverse/binary-i386/Packages.gz)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
root@hasox:/etc/apt#

---

### Post by Mustard on 2006-03-30
Take your password out of the previous post. :)

If my report to the mods goes through, can you change the the text just after <removed username> to xxxxxx or something please?  The password is currently visible for all to see.

---

### Post by nocturn on 2006-03-30
I have taken out both the usernama and password.

---

### Post by Mustard on 2006-03-30
[QUOTE=nocturn]I have taken out both the usernama and password.[/QUOTE]

Thanks for responding so quickly, nocturn. :)

---

### Post by Mustard on 2006-03-30
> **5jarinko]same problem,

root@hasox:/etc/apt# cat apt.conf
APT::Authentication::TrustCDROM "true" said:**
> http://archive.ubuntu.com/ubuntu/dists/breezy-updates/universe/binary-i386/Packages.gz[/url]  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy-updates/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy-updates/multiverse/binary-i386/Packages.gz)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
root@hasox:/etc/apt#


You might have to 'touch' the file after editing?

```
touch /etc/apt/apt.conf
```

I can't think of any secure method for doing this off the top of my head.  The method I would use it to edit my .bashrc to include the proxy, but it means your password is going to be in a file accesible from your user account. I guess this no more problematic  than the .wvdial.conf file I have in my home directory with my ISP password sitting in it. 

There are instructions for doing this via the .bashrc on this wiki page (at the bottom of the page)...

[https://wiki.ubuntu.com/AptGetHowto](https://wiki.ubuntu.com/AptGetHowto)

I never had much luck getting it to work using apt-conf.  When I looked for my apt.conf file I didnt even have one.  If you manage to get it working via apt.conf please post your solution, so that I can edit the wiki entry above to show that method.

---

### Post by Mustard on 2006-03-30
Hmmm..well I think I have it working via apt-conf now, which is not much help with your problem I know, but at aleast I can edit the wiki to include instructions for it now. :)

-edit-

Bah!  The wiki authentication has gone down just as I am about to edit it..just my luck. :D

---

### Post by Mustard on 2006-03-30
Another method of using a proxy via command line is to use this syntax.

```
export HTTP_PROXY=proxyserver:port
```

Again this is going to be an insecure method for you to use, as when you type this into the command line, its going to be stored in the .bash_history file, so again your password is going to be visible in plain text from your user account.

---

### Post by Mustard on 2006-03-30
Can anyone make any sense of these Debian instructions for authenticating?

```
// HTTP method configuration
  http
  {
    Proxy "http://127.0.0.1:3128";
    Proxy::http.us.debian.org "DIRECT";  // Specific per-host setting
    Timeout "120";
    Pipeline-Depth "5";

    // Cache Control. Note these do not work with Squid 2.0.2
    No-Cache "false";
    Max-Age "86400";     // 1 Day age on index files
    No-Store "false";    // Prevent the cache from storing archives
  };

  ftp
  {
    Proxy "ftp://127.0.0.1/";
    Proxy::http.us.debian.org "DIRECT"; // Specific per-host setting

    /* Required script to perform proxy login. This example should work
       for tisfwtk */
    ProxyLogin
    {
       "USER $(PROXY_USER)";
       "PASS $(PROXY_PASS)";
       "USER $(SITE_USER)@$(SITE):$(SITE_PORT)";
       "PASS $(SITE_PASS)";
    };

```

The problem with the above script is it seems to be set up to authenticate with an ftp proxy, rather than a http proxy.  It all looks like goobly-gook to me.  I've been googling extensively for an hour now and I can't find a single reference or forum discussion that actually makes any sense to me. :D

These instructions are provided by Debian here on my system..

```
/usr/share/doc/apt/examples/configure-index.gz
```

I found this manual page which seems to make some sense, but from what I read the above syntax used by the OP is correct and should work.

[http://www.die.net/doc/linux/man/man5/apt.conf.5.html](http://www.die.net/doc/linux/man/man5/apt.conf.5.html)

---

### Post by 5jarinko on 2006-03-30
doesnt work

---

### Post by 5jarinko on 2006-03-30
still does not work

---

### Post by Mustard on 2006-03-30
[QUOTE=5jarinko]still does not work[/QUOTE]

Unfortunately, that is telling me nothing.  What doesnt work?  Using what method?

---

### Post by 5jarinko on 2006-03-30
I need to set up my shell or file apt.conf to proxy with authentification,
so any export proxy_http=http://ip_adress:port does not work,
in my browser when I start first time firefox I have to go with my login and password, but usually export proxy_http=http://login:password@ip_adress:port 
ist working, and my authentification via firefox is correct

---


---
title: "Unable to download software updates"
date: 2006-07-27
forum: Absolute Beginner Talk
---

### Post by rmsh on 2006-07-27
Hi

I've recently installed Ubuntu (Dapper) in a virtual m/c running in my laptop. I'm behind proxy that needs authentication. 

I've entered Proxy details in 3 different locations
[LIST]
[*]System > Preferences >Network Proxy

[*]Exported env variable http_proxy as [http://user:password@proxy.domain.com:port](http://user:password@proxy.domain.com:port)
[*]/etc/apt/apt.conf as Acquire::http::Proxy "http://user:password@proxy.domain.com:port"
[/LIST]

Ubuntu tells me that there are 130 updates available in a bubble window. But when I try to install them via the regular "Software Updates", I get an error "407 Proxy Authentication Required".

Ofcourse I'm connected to internet, this post is from Firefox under ubuntu. I've made sure that the passwords are correct and rebooted the system to see if that helps. 

Any help is highly appreciated.

- Ramesh

---

### Post by avtolle on 2006-07-27
[http://www.ubuntuforums.org/showthread.php?t=183093&page=2](http://www.ubuntuforums.org/showthread.php?t=183093&page=2) may be of some assistance to you, if you haven't already looked at it.

---

### Post by rmsh on 2006-07-27
Tried everything that is mentioned in the previous thread to vain. :(

---


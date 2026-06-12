---
title: "Setting up proxy so i can apt-get"
date: 2005-10-25
forum: Absolute Beginner Talk
---

### Post by bete on 2005-10-25
Where my linux computer is, i have to use a proxy to surf with web browsers. I need that for apt-get aswell..
So i was wondering, is there any way to set up a proxy for apt-get in terminal or in X?
:KS :KS :KS

---

### Post by UbuWu on 2005-10-25
You can set one in the synaptic preferences. Don't know if that setting is used for apt-get as well.

---

### Post by lreyes6 on 2005-10-25
why u don't use the environmental proxy settings?
just go to System --> Preferences --> Network proxy

that should work

---

### Post by A-star on 2005-10-27
and if you don't have a gui, what do you do then?

---

### Post by bete on 2005-10-27
[QUOTE=A-star]and if you don't have a gui, what do you do then?[/QUOTE]


If you know your proxy settings there should be a way to do it..
It diddnt work for me but that was because the network here is totally closed..

Anyways

Create a file in /etc/apt/ called apt.conf 
```
vi /etc/apt/apt.conf

```

Now go into the file by doing :
```
sudo nano /etc/apt/apt.conf
```

In there you shall write  (case sensitive):
```
Aquire::http::Proxy "http://yourproxyipaddress";
```
Then do ctrl+x and press "Y" to save, then enter.

Try doing
```
sudo apt-get update
```
and see if it worked.

---

### Post by dvejnovic on 2005-10-27
[QUOTE=A-star]and if you don't have a gui, what do you do then?[/QUOTE]

in /etc/profile at the end add:

http_proxy="http://authproxyname:authproxypasswd@proxyname:proxyport/"
EXPORT http_proxy

Example for http_proxy:
http_proxy="http://name:passwd@www.proxy.com:3128/"

This should work...:cool:

---

### Post by public_void on 2005-10-27
Yet another apt.conf, this is how mine looks, works great.

ACQUIRE {
http::proxy "http://username:password@proxy:port/"
}

---


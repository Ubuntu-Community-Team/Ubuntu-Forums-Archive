---
title: "Can't find etter.conf file"
date: 2007-12-18
forum: Absolute Beginner Talk
---

### Post by Fanatico on 2007-12-18
I run Ubuntu desktop 7.1. I downloaded sources of Ettercap and was trying to build them without success. Then I simply have installed latest Ettercap via Synaptic packet manager.

Now I am trying to configure Ettercap and can't find etter.conf file.
I was told it should be in /usr/local/etc. But there is no any etter.conf there.

I tried to search for etter.conf with help of following command:
sudo find / -name etter.conf
I did found etter.conf in other directory where I copied sources and tried to build Ettercap.

Can anyone explain where is etter.conf located and what could be went wrong with my Ettercap?

Thanks

---

### Post by Severun on 2007-12-18
In Ubuntu things go in /usr or /etc or /usr/share

Some systems put things in /usr/local or /usr/local/etc or /usr/local/share respectively

From seeing how other apps install I would imagine your config file is probably in 

/etc/ettercap  other config files go there, like /etc/apache2/apache2.conf, /etc/php5/cli/php.ini, etc.

It proabably got named etter.conf.default or some such thing and you have to copy it to etter.conf and put your own config info in.

I'm just guessing based on past experience with installing other applications and going "Where is that dang config file".  Hope this helps.

---


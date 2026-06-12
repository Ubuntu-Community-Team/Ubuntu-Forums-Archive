---
title: "fixing the proxy settings in firefox."
date: 2007-09-11
forum: Absolute Beginner Talk
---

### Post by sys_alpha on 2007-09-11
The problem that i am facing nowadays is to fix a proxy settings for mozilla.
I want that the lan users under my server could not change the settings of proxy given to them by me.
I have seen the .js files and tried to change the write permissions of this file so that except root nobody can't change this.
But that failed..
Do Reply if you know how to?

---

### Post by tvrg on 2007-09-11
I think the best way to do something like that is to configure a transparent proxy for your lan, then even without proxy settings the requests will go through that proxy. Then block some outgoing ports on your firewall to prevent them from going out in another manner.

Otherwise it's very hard to control everything (lynx, firefox from a thumb drive etc...)

check this url [http://www.cyberciti.biz/tips/linux-setup-transparent-proxy-squid-howto.html](http://www.cyberciti.biz/tips/linux-setup-transparent-proxy-squid-howto.html) or google transparent proxy for more info

---


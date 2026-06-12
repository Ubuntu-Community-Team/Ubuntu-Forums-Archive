---
title: "Web pages not loading"
date: 2006-12-03
forum: Absolute Beginner Talk
---

### Post by SteveJ on 2006-12-03
Hello;

Finally got Ubuntu to install. I used the alternate install - that seemed to work much better than trying to run GUI on a CD. Aside from the fact that I messed up my Windows XP boot (I'm dealing with that on another post), I am having problems with Firefox. 

I can only open some web pages - and very slow at that. Google and ebay load but many others, including [www.ubuntu.com](www.ubuntu.com) don't load at all. 

Any suggestions?

Thanks;

Stevej

---

### Post by mssever on 2006-12-03
> **SteveJ said:**
> Hello;

Finally got Ubuntu to install. I used the alternate install - that seemed to work much better than trying to run GUI on a CD. Aside from the fact that I messed up my Windows XP boot (I'm dealing with that on another post), I am having problems with Firefox. 

I can only open some web pages - and very slow at that. Google and ebay load but many others, including [www.ubuntu.com]("http://www.ubuntu.com") don't load at all. 

Any suggestions?

Thanks;

StevejDisabling IPv6 in Firefox works for some people in this situation. I don't have any direct knowledge here, but it's worth a try.

Type about:config into Firefox's address bar, then find network.dns.disableIPv6 and set it to true. See if that helps.

---

### Post by SteveJ on 2006-12-03
Thanks, that did the trick for me. 

SteveJ

---


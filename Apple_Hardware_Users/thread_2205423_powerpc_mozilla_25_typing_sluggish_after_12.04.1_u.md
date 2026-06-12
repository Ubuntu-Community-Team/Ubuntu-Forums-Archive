---
title: "powerpc mozilla 25: typing sluggish after 12.04.1 upgrade"
date: 2014-02-13
forum: Apple Hardware Users
---

### Post by franklynb on 2014-02-13
I upgraded to the 2-06-14 release of 12.04 day before yesterday. Last night I noticed that Mozilla had slowed to a crawl, with sluggish
window launching and updates, and maddeningly slow typing response.

A little research turns out that xul-ext-ubufox <https://launchpad.net/ubuntu/precise/powerpc/xul-ext-ubufox/2.7-0ubuntu0.12.04.1>
an "add-on" that links to ubuntu and manages a few other non-critical :popcorn: browser updates is the culprit. There is even a warning
on the launchad page.

'ubufox' can be disabled from the Add-Ons/Extensions menu; or
 
**$sudo apt-get remove xul-ext-ubufox**

which is what I did. Mozilla got well, immediately.

--frankb

powerpc G5x4CPU watercooled, ubuntu precise 12.04,3.2.0-58-powerpc64-smp

---


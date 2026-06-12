---
title: "MBP set to &quot;ondemand&quot;, defaults to &quot;performance&quot; on fresh boot-up. How stop this?"
date: 2009-09-21
forum: Apple Hardware Users
---

### Post by swarup on 2009-09-21
I have my MBP 15,2 (Jaunty) set to "ondemand", but despite this, it often sets itself to "performance" when I boot it up, so that I have to reset it to "demand". Have others experienced this? What is the way to get the "ondemand" setting to stick?

---

### Post by _mario_ on 2009-09-22
> **swarup said:**
> I have my MBP 15,2 (Jaunty) set to "ondemand", but despite this, it often sets itself to "performance" when I boot it up, so that I have to reset it to "demand". Have others experienced this? What is the way to get the "ondemand" setting to stick?

if you have laptop-mode-tools installed and enabled, you might check its configuration in /etc/laptop-mode/conf.d/cpufreq.conf. Otherwise /etc/init.d/ondemand should always enable the ondemand CPU frequency governor, unless some desktop applet sets something different.

ciao,
Mario

---


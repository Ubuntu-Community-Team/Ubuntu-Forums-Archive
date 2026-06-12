---
title: "Speed up Firefox"
date: 2007-10-10
forum: Absolute Beginner Talk
---

### Post by Jimmyfj on 2007-10-10
Don't know if this belongs in the beginners section. If not someone may move it to the right place.

If you find that your Firefox is somewhat slow I've found a small and easy to do "tweak" that will speed up your Firefox.

First we need to open the Firefox config. Start your Firefox and at the address line type the following command:

```
about:config
```

Next we need to set three settings in the config file:

1: Find the setting **network.http.pipelining** this must bet set to True
2 : find the setting **network.http.proxy.pipelining** this must be set to True
3 : find the setting **network.http.pipelining.maxrequests** this must be set to 40

Close your Firefox browser after making these changes and open a new session of Firefox. Now you should be able to measure a significant difference in speed.

---

### Post by kerry_s on 2007-10-10
my user.js

```

user_pref("network.http.max-connections", 48);
user_pref("network.http.max-connections-per-server", 32);
user_pref("network.http.max-persistent-connections-per-proxy", 20);
user_pref("network.http.max-persistent-connections-per-server", 16);
user_pref("network.http.pipelining", true);
user_pref("network.http.proxy.pipelining", true);
user_pref("network.http.pipelining.maxrequests", 8);
user_pref("nglayout.initialpaint.delay", 0);
user_pref("network.http.keep-alive.timeout", 30);
user_pref("network.http.request.max-start-delay", 4);
user_pref("network.http.connect.timeout", 30);
user_pref("network.dnsCacheExpiration", 60);
user_pref("network.dnsCacheEntries", 20);
user_pref("network.ftp.idleConnectionTimeout", 60);
user_pref("browser.cache.disk.capacity", 100000);
user_pref("browser.cache.disk_cache_ssl", true);
user_pref("browser.chrome.toolbar_tips", false);
user_pref("mousewheel.horizscroll.withnokey.action", 1);
user_pref("network.dns.disableIPv6", true);
user_pref("browser.link.open_newwindow", 3);

```

---


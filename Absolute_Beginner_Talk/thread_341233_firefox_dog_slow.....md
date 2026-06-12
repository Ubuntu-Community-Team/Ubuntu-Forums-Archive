---
title: "firefox dog slow...."
date: 2007-01-18
forum: Absolute Beginner Talk
---

### Post by old_dog on 2007-01-18
I have just installed an adsl router modem after never getting speedtouch modem to work. Well it works but it is dog slow.... Dual boot m/c in Windows page loads in a blink of an eye, in Ubuntu dapper drake 3 or 4 minutes painful or wot! I've seen other people have had the same problem....but didn't understand the answers. Spell it out for me what do I have to look for and change and where?????
Cheers

---

### Post by deadgobby on 2007-01-18
Do you run Firefox in Windows? Any how here a link to speed up Firefox.
[https://wiki.ubuntu.com/FirefoxTipsAndTricks?highlight=%28firefox%29#](https://wiki.ubuntu.com/FirefoxTipsAndTricks?highlight=%28firefox%29#)
look at  #2
Gobby

---

### Post by zephyrus54 on 2007-01-20
Type "about:config" into your url/address bar.

Look for the entry "network.dns.disableIPv6"

If the value is set at "false", right click on the entry and select toggle so that the value is now set at "true".

This was a problem for me at first too, so hopefully this fixes the slowness problem for you.  It seems as though some routers don't work well with Ipv6 (That's the extent of my knowledge, so don't ask for any further explanations =P)

---

### Post by permieshane on 2007-01-25
Thanks zephyrus54,
I just tried your suggestion & now firefox flies!

---


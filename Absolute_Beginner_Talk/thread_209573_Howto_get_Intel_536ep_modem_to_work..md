---
title: "Howto get Intel 536ep modem to work."
date: 2006-07-05
forum: Absolute Beginner Talk
---

### Post by editrix on 2006-07-05
I'd have added this to the original thread 
[http://www.ubuntuforums.org/showthread.php?t=171284&highlight=intel536](http://www.ubuntuforums.org/showthread.php?t=171284&highlight=intel536)
but that forum's closed.

I had the modem working fine in Gnome Dapper. It's an excellent HOWTO. Then I installed Kubuntu-Desktop and KPPP can't find the modem. Nor can pon. There's no /dev/536ep0, so I guess that's why the symlink in  /etc/udev/rules.d/10-local.rules doesn't work. :-)

I'm not sure there ever was a file 536ep0 in /dev, just assuming, but ...

Anybody else have this happen? What does one do?

---


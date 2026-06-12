---
title: "[SOLVED] How to run as root to update Firefox?"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by GkProf on 2007-10-19
In 7.04, I'm running Firefox v. 2.0.0.6, and would like to update to the newest 2.0.0.8, but the update options are grayed out. My *guess* is that might be because I need to run as root to update? I activated the root account (sudo passwd root), then logged in as root in Terminal, but though Firefox opened as a new user, the update is still grayed out.

I must be doing something wrong. Any ideas? Is there an easier way to update Firefox?

Thanks.

---

### Post by BOZG on 2007-10-19
[http://ubuntuzilla.wiki.sourceforge.net/]("http://ubuntuzilla.wiki.sourceforge.net/")

It's simple and can be set to notify about updates.  Just install and run in terminal with "ubuntuzilla.py".

---

### Post by p_quarles on 2007-10-19
No, Ubuntu uses a special build of Firefox. That's why the update is greyed out. When Ubuntu releases a new version, the update manager will take care of it automatically. 

Basically, even if you don't have the numerically latest version of Firefox, you still have all the security patches that the regular version has. It just has a different number.

---

### Post by GkProf on 2007-10-19
OK, thanks. I've now got the ...8 version installed and running. And I think I've got the ubuntuzilla update checker set to run automatically.

---

### Post by benerivo on 2007-10-19
> **p_quarles said:**
> No, Ubuntu uses a special build of Firefox. That's why the update is greyed out. When Ubuntu releases a new version, the update manager will take care of it automatically. 

Basically, even if you don't have the numerically latest version of Firefox, you still have all the security patches that the regular version has. It just has a different number.

Are you sure this is true? Mozilla only released 2.0.0.8 on Oct 18th. This [new version patched a security flaw]("http://www.mozilla-europe.org/en/products/firefox/2.0.0.8/releasenotes/"). How and when does the Ubuntu build get this patch, whilst it remains at 2.0.0.6.

---

### Post by mc4man on 2007-10-19
For future use when the updater informs you of new release use
```
gksudo firefox &
``` to open firefox with update option enabled

---


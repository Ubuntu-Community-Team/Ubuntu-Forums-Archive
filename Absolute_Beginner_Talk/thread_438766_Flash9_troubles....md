---
title: "Flash9 troubles..."
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by isaacj87 on 2007-05-10
Okay...so yes I'm bored and nitpicking here, but I was wondering why certain websites can't completely load. For example, Scion.com or Toyota.com don't show up on my comp...am I missing something?

haha thanks in advance!

---

### Post by zvacet on 2007-05-10
Do you have flushplugin-nonfree installed?I think you can find it in repos.

---

### Post by apienk01 on 2007-05-10
You have probably installed one of the replacements of the proprietary Adobe Flash plugin, eg. libflash, gnash. Neither of them fully supports Flash. Uninstall them, and install flashplugin-nonfree from the multiverse repository. This won't work if you use 64-bit (AMD64, x86_64) Ubuntu distribution, because flashplugin-nonfree is 32-bit only. Not all is lost however. 32-bit Mozilla plugins can be installed in 64-bit Firefox using nspluginwrapper package. It works perfectly!

---


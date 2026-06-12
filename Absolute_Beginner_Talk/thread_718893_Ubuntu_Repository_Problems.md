---
title: "Ubuntu Repository Problems"
date: 2008-03-08
forum: Absolute Beginner Talk
---

### Post by Mantulen on 2008-03-08
Ok I installed Windows XP and Ubuntu 7.10 from scratch on a single hard drive into a dual boot configuration. Windows XP works great.  The problem is Ubuntu:

The internet works great, I can go on firefox and browse the web and Pidgin Instant messenger client works too.  All applications that need the internet seem to work fine EXCEPT:

- Ubuntu update
- Add/Remove programs (I can not install any new programs, it says the list is out of date and it can't seem to get a new list)
- And finaly when I go to youtube in firefox, it can't download the flash-plugin.  It says something like "Can not find adobeflash-nonfree".

If this makes any difference, I am using my home Wifi connection.

What seems to be the problem?

---

### Post by PeterJS on 2008-03-08
Was you internet connection setup when you first installed? Gutsy makes some bad assumptions about your internet connection if it can't find it when it was first installed. To fix this you'll want to tell it that it can get updates from the internet. In System > Administration > Software Sources make sure that the four check boxes for the main repositories are check, the fifth one (source) is optional and really only useful if you're wiriting updates for ubuntu.

---


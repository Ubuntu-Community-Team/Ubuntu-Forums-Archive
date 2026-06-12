---
title: "&quot;Update&quot; of OpenOffice suite, should I?"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by mkendall on 2008-02-12
After installing Ubuntu 7.10, I saw that Open Office was v2.0. After doing some searching in the internet tubes, I followed some instructions for installing OO from OpenOffice.org. Having done that, the Update Manager now tells me there are 13 updates available, "updating" from version 2.3.1-9238 to 1:2.3.0-1ubuntu5.3. 

Is this actually an update, is it merely a relabeling of the same thing, or does the manager just not like that I have a version it doesn't. If it is not an update, how can I tell the manager to ignore it?

Thanks

Matthew

---

### Post by edmund on 2008-02-12
The problem could be that OO was originally installed from the Ubuntu repository, then you installed it using binaries from the OO website.  The software in the Ubuntu repositories will generally be a few versions behind the most recent version available directly from  the website.  So now Update Manager is confused because it was bypassed when you installed OO.

It might be easiest to de-install OO using Ubuntu Add/Remove applications, if that's still possible, then re-install using the same.  From then on, Update Manager won't be confused, though you'll have to accept always being a few versions behind the latest.

---

### Post by Hagar Delest on 2008-02-12
Had you completely uninstalled the Ubuntu version of OOo? Weird if you've been able to install the official version in parallel with the Ubuntu one.

---


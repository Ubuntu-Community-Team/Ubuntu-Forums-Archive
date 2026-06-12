---
title: "GUI Interface to fstab?"
date: 2005-12-14
forum: Absolute Beginner Talk
---

### Post by TheOrangeRider on 2005-12-14
Hi there,

Does Ubuntu have any tool that provides a nice GUI interface to allow me to add mounts in the fstab file? I've been looking for it in the menu options but haven't seen anything yet.

Thanks!

---

### Post by Kyral on 2005-12-14
There *is *but I have heard bad things about it... Its actually faster to edit the thing yourself. Pop it open (using your favorite editor as root) and the syntax for the line is

```
<device name> <mountpoint> <filesystem (If you don't know it, set it to auto and note what the system says it is) > <options (You'll most likely want to set defaults, auto(if its a HD), rw, users> 0 0
```

---

### Post by TheOrangeRider on 2005-12-14
Yeah I guess that wasn't so bad. Thanks for the help!

---

### Post by thor918 on 2007-06-29
> **Kyral said:**
> There *is *but I have heard bad things about it... Its actually faster to edit the thing yourself. Pop it open (using your favorite editor as root) and the syntax for the line is

```
<device name> <mountpoint> <filesystem (If you don't know it, set it to auto and note what the system says it is) > <options (You'll most likely want to set defaults, auto(if its a HD), rw, users> 0 0
```

It's not always so fast to edit fstab manually.
infact in my system where I have to use uuid's to define
every hd, including one for every partition, and I have 8 HD.. editing fstab gets like an nightmare!
I just wish one could add mounting capabilities to gparted! it would have been so much easier then.

---

### Post by seandiggity on 2008-01-09
The only GUI for fstab I know of is here: [http://pysdm.sourceforge.net](http://pysdm.sourceforge.net) and it's in the universe repos: [http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&version=all&exact=1&keywords=pysdm](http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&version=all&exact=1&keywords=pysdm)

---

### Post by dcstar on 2008-01-09
> **TheOrangeRider said:**
> Hi there,

Does Ubuntu have any tool that provides a nice GUI interface to allow me to add mounts in the fstab file? I've been looking for it in the menu options but haven't seen anything yet.

Thanks!

Install the** pysdm** package, then System-Administration-Storage Device Manager.

---


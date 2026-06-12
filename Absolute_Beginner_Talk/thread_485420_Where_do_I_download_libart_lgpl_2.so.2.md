---
title: "Where do I download libart_lgpl_2.so.2?"
date: 2007-06-26
forum: Absolute Beginner Talk
---

### Post by Johnny K on 2007-06-26
Alot of applications aren't working properly because they are missing "libart_lgpl_2.so.2". For example, typing *sunbird.sh* in terminal gives the following error:
```
Gtk-Message: Failed to load module "gail": libart_lgpl_2.so.2: cannot open shared object file: No such file or directory
```
Where can I find libart_lgpl_2.so.2? A synaptic search brings up nothing.

As always, thanks in advance. :p

---

### Post by Sparkster185 on 2007-06-26
You might want to try one of these.  I'm not exactly which one you need, but you can always uninstall what's unnecessary.

[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=libart&searchon=names&subword=1&version=feisty&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=libart&searchon=names&subword=1&version=feisty&release=all)

---

### Post by Johnny K on 2007-06-26
> **Sparkster185 said:**
> You might want to try one of these.  I'm not exactly which one you need, but you can always uninstall what's unnecessary.

[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=libart&searchon=names&subword=1&version=feisty&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=libart&searchon=names&subword=1&version=feisty&release=all)
I already have libart-2.0-2 installed, so I know I must need something else. I tried libart2, but that didn't work. Is there a way I can better find out which one I need, or should I just keep trying different ones?

---

### Post by Johnny K on 2007-06-28
I just realized that I do have /usr/lib/libart_lgpl_2.so.2 installed. It links to /usr/lib/libart_lgpl_2.so.2.3.17. The permissions for both are:
Owner (root) - Read and Write
Group (root) - Read only
Others - Read only

Yet Sunbird and Thunderbird still give the error "Gtk-Message: Failed to load module "gail": libart_lgpl_2.so.2: cannot open shared object file: No such file or directory"

Any idea what I'm doing wrong? Do I have to change the permissions?

---


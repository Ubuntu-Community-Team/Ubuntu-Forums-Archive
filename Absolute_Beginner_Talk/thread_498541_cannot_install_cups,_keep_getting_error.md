---
title: "cannot install cups, keep getting error"
date: 2007-07-11
forum: Absolute Beginner Talk
---

### Post by gnychis on 2007-07-11
Hi all,

I had cups installed but was having problems with lpr.  So I wanted to remove cups completely so I did:

```

sudo apt-get autoremove cupsys cupsys-client

```

Then i wanted to blast away all config files to start clean:
```

rm -fr /etc/cups

```

Now I cannot install either:
```

gnychis@cyprus:~/school/wireless_cd/trunk/code/ns_code/mac$ sudo apt-get install cupsys cupsys-client
Reading package lists... Done
Building dependency tree       
Reading state information... Done
cupsys is already the newest version.
cupsys-client is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up cupsys (1.2.8-0ubuntu8) ...
chown: cannot access `/etc/cups/cupsd.conf': No such file or directory
dpkg: error processing cupsys (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 cupsys
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Yes, I understand that there is no config file.  Shouldn't it be installing one?  How else is cups supposed to install if it depends on a file that is in its own package?

---

### Post by DBStevens on 2007-07-11
What did the remove do?

The system still says 

cupsys is already the newest version.
cupsys-client is already the newest version.

I think you need to rebuild your installed package information however that gets done. 

It looks like it was never removed as far as the package system is concerned so it did things in the wrong sequence or attempted to do things it shouldn't have.

---


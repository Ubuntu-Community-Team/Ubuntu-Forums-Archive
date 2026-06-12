---
title: "[SOLVED] libcurl3 unmet dependency"
date: 2007-11-19
forum: Absolute Beginner Talk
---

### Post by pfwd.tech on 2007-11-19
This is a pain.  I haven't been able to fix this for about a month now.
I'm trying to reinstall rtorrent and it keeps says that i have an unmet dependency
```

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  libcurl3-openssl-dev: Depends: libcurl3 (= 7.15.5-1ubuntu2) but 7.16.4-2ubuntu1 is to be installed
E: Broken packages

```
I've uninstalled rtorrent and libtorrent and then tried reinstalling them but keep getting this message.
I then tried:
```
apt-get -f install
```
and still no luck.

Any one have any ideas on what i can do?

---

### Post by pfwd.tech on 2007-11-20
I found out that i was still using old Fesity repos. I removed these and reinstalled rtorrent and it works fine

---


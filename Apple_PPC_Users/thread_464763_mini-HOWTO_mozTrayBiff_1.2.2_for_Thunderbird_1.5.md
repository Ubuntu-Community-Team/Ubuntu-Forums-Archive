---
title: "mini-HOWTO: mozTrayBiff 1.2.2 for Thunderbird 1.5"
date: 2007-06-05
forum: Apple PPC Users
---

### Post by eugoss on 2007-06-05
It's easy to build [_the mozTrayBiff extension_]("http://moztraybiff.mozdev.org/") for Thunderbird 1.5 under Ubuntu 7.04 PPC. Here is a simple how-to:

[LIST=1]
[*]Install the following packages if they are not installed yet.
```
apt-get install g++ libgtk2.0-dev mozilla-thunderbird-dev
```
[*]Download *mozTrayBiff-1.2.2.tar.gz* from the site ([http://downloads.mozdev.org/moztraybiff/mozTrayBiff-1.2.2.tar.gz](http://downloads.mozdev.org/moztraybiff/mozTrayBiff-1.2.2.tar.gz)) and unpack the archive.
[*] Call the following command from the unpacked *mozTrayBiff-1.2.2 *directory:
```
make MOZILLA_PLATFORM=tbird REAL_CONFIG=/usr/bin/mozilla-thunderbird-config MOZ_TRUNK=1
```
[*]Pick the fresh XPI file ;)
[/LIST]

---


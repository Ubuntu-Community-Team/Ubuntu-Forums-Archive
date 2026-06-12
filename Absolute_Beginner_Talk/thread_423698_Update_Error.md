---
title: "Update Error"
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by bootslap on 2007-04-26
Hi, I was wondering if anybody could tell me how to overcome this update error.

It says:

Could not download all repository indexes

The repository might be no longer available or could not be ocntacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.


[http://in.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz:](http://in.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz:) Sub-process gzip returned an error code (1)
[http://in.archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.gz:](http://in.archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.gz:) Sub-process gzip returned an error code (1)


Any suggestions would be appreciated....

---

### Post by AtrejuT on 2007-04-26
> **bootslap said:**
> Hi, I was wondering if anybody could tell me how to overcome this update error.

It says:

Could not download all repository indexes

The repository might be no longer available or could not be ocntacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.


[http://in.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz:](http://in.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz:) Sub-process gzip returned an error code (1)
[http://in.archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.gz:](http://in.archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.gz:) Sub-process gzip returned an error code (1)


Any suggestions would be appreciated....

That seems to be a problem with the indian (?) mirror. It might be fixed just by waiting. You could however also try the international mirror by removing the .in in the file /etc/apt/sources.list:
```

gksu gedit /etc/apt/sources.list

```
then find occurences of
in.archive.ubuntu.com
and replace them by
archive.ubuntu.com

---

### Post by bootslap on 2007-04-26
Thanks for your response .... I thought that I had missed out on checking something ... Really appreciate that.

---


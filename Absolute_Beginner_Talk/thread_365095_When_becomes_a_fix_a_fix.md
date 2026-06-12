---
title: "When becomes a fix a fix"
date: 2007-02-19
forum: Absolute Beginner Talk
---

### Post by beste on 2007-02-19
Hi all,

I am dealing with two bugs in edgy, which both have been identified and - from what I can determine - have been committed to being fixed.

See:
[https://launchpad.net/ubuntu/+source/ubuntu-docs/+bug/67111](https://launchpad.net/ubuntu/+source/ubuntu-docs/+bug/67111)
and
[https://launchpad.net/ubuntu/+source/ubuntu-docs/+bug/68818](https://launchpad.net/ubuntu/+source/ubuntu-docs/+bug/68818)

However, I cannot see new packages for updating those two packages.

Is there any secret switch/configuration I have to do in order to see the updates? Or is the explanation as easy as: There are no updates available, yet!

If the latter is the case, can I determine somehow, when those updates could become available?

With best regards,

Robert

---

### Post by an.echte.trilingue on 2007-02-19
When the red "confirmed" changes to "fix released", the fix will be done in Ubuntu.  In the mean time, you can install the dapper version (which does not have the bug) like this:

1.  Add these line to /etc/apt/sources.list
```
deb-src http://archive.ubuntu.com/ubuntu/ dapper universe multiverse
deb http://security.ubuntu.com/ubuntu dapper-security universe multiverse
```

2.  Add this to /etc/apt/preferences (create file if it does not exist):
```
     Package: squid
     Pin: release a=dapper
     Pin-Priority: 1001
```

3. Then
```
sudo apt-get update
sudo apt-get upgrade
```

Take care
-mat

---

### Post by beste on 2007-02-19
Hi,

thanks I appreciate your input.

I had removed squid from my system. Then I added the sources and the preferences.

I did an apt-get update

but now, when I want to apt-get install squid it says:

Reading package lists... Done
Building dependency tree
Reading state information... Done
Package squid is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package squid has no installation candidate


Any more help?

---

### Post by beste on 2007-02-20
the problem was, the squid package doesn't seem to be in:

deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse

When I added:

# Ubuntu supported packages
# GPG key: 437D05B5
deb [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) dapper main restricted
deb [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

deb-src [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) dapper main restricted
deb-src [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

# Ubuntu community supported packages
# GPG key: 437D05B5
deb [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) dapper universe multiverse
deb [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) dapper-updates universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse

deb-src [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) dapper universe multiverse
deb-src [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) dapper-updates universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse

to my sources.list it worked.

Thanks again for your help, mat!

---


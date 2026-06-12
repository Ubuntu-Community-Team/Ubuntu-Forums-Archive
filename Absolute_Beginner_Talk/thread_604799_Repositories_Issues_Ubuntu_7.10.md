---
title: "Repositories Issues Ubuntu 7.10"
date: 2007-11-06
forum: Absolute Beginner Talk
---

### Post by abc12345 on 2007-11-06
Hi,

I'm new to Linux and Ubuntu. I installed Ubuntu on my HP laptop and during installation I got an error stating that securities repository cannot be accessed. 

I opened the sources.list file and I see the following error message

# Line commented out by installer because it failed to verify:
deb-src [http://us.archive.ubuntu.com/ubuntu/dists](http://us.archive.ubuntu.com/ubuntu/dists) gutsy main restricted

# Line commented out by installer because it failed to verify:
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted

Would appreciate any help in resolving this issue.

Thanks

---

### Post by ardchoille42 on 2007-11-06
I get the same error now and then, simply wait a bit and do:

```

sudo apt-get update

```

---

### Post by abc12345 on 2007-11-06
I have been trying this since yesterday. I did a reload from the Synaptic Package Manager and I get the following error

[http://us.archive.ubuntu.com/ubuntu/dists/dists/gutsy/Release.gpg:](http://us.archive.ubuntu.com/ubuntu/dists/dists/gutsy/Release.gpg:) Could not resolve 'us.archive.ubuntu.com'
[http://us.archive.ubuntu.com/ubuntu/dists/dists/gutsy/main/i18n/Translation-en_US.bz2:](http://us.archive.ubuntu.com/ubuntu/dists/dists/gutsy/main/i18n/Translation-en_US.bz2:) Could not resolve 'us.archive.ubuntu.com'
[http://us.archive.ubuntu.com/ubuntu/dists/dists/gutsy/restricted/i18n/Translation-en_US.bz2:](http://us.archive.ubuntu.com/ubuntu/dists/dists/gutsy/restricted/i18n/Translation-en_US.bz2:) Could not resolve 'us.archive.ubuntu.com'
[http://us.archive.ubuntu.com/ubuntu/dists/dists/gutsy/universe/i18n/Translation-en_US.bz2:](http://us.archive.ubuntu.com/ubuntu/dists/dists/gutsy/universe/i18n/Translation-en_US.bz2:) Could not resolve 'us.archive.ubuntu.com'
[http://us.archive.ubuntu.com/ubuntu/dists/dists/gutsy/multiverse/i18n/Translation-en_US.bz2:](http://us.archive.ubuntu.com/ubuntu/dists/dists/gutsy/multiverse/i18n/Translation-en_US.bz2:) Could not resolve 'us.archive.ubuntu.com'
[http://us.archive.ubuntu.com/ubuntu/dists/dists/gutsy-updates/Release.gpg:](http://us.archive.ubuntu.com/ubuntu/dists/dists/gutsy-updates/Release.gpg:) Could not resolve 'us.archive.ubuntu.com'
[http://us.archive.ubuntu.com/ubuntu/dists/dists/gutsy-updates/main/i18n/Translation-en_US.bz2:](http://us.archive.ubuntu.com/ubuntu/dists/dists/gutsy-updates/main/i18n/Translation-en_US.bz2:) Could not resolve 'us.archive.ubuntu.com'
[http://us.archive.ubuntu.com/ubuntu/dists/dists/gutsy-updates/restricted/i18n/Translation-en_US.bz2:](http://us.archive.ubuntu.com/ubuntu/dists/dists/gutsy-updates/restricted/i18n/Translation-en_US.bz2:) Could not resolve 'us.archive.ubuntu.com'
[http://us.archive.ubuntu.com/ubuntu/dists/dists/gutsy-updates/universe/i18n/Translation-en_US.bz2:](http://us.archive.ubuntu.com/ubuntu/dists/dists/gutsy-updates/universe/i18n/Translation-en_US.bz2:) Could not resolve 'us.archive.ubuntu.com'
[http://us.archive.ubuntu.com/ubuntu/dists/dists/gutsy-updates/multiverse/i18n/Translation-en_US.bz2:](http://us.archive.ubuntu.com/ubuntu/dists/dists/gutsy-updates/multiverse/i18n/Translation-en_US.bz2:) Could not resolve 'us.archive.ubuntu.com'
[http://us.archive.ubuntu.com/ubuntu/dists/dists/gutsy-backports/Release.gpg:](http://us.archive.ubuntu.com/ubuntu/dists/dists/gutsy-backports/Release.gpg:) Could not resolve 'us.archive.ubuntu.com'
[http://us.archive.ubuntu.com/ubuntu/dists/dists/gutsy-backports/main/i18n/Translation-en_US.bz2:](http://us.archive.ubuntu.com/ubuntu/dists/dists/gutsy-backports/main/i18n/Translation-en_US.bz2:) Could not resolve 'us.archive.ubuntu.com'
[http://us.archive.ubuntu.com/ubuntu/dists/dists/gutsy-backports/restricted/i18n/Translation-en_US.bz2:](http://us.archive.ubuntu.com/ubuntu/dists/dists/gutsy-backports/restricted/i18n/Translation-en_US.bz2:) Could not resolve 'us.archive.ubuntu.com'
[http://us.archive.ubuntu.com/ubuntu/dists/dists/gutsy-backports/universe/i18n/Translation-en_US.bz2:](http://us.archive.ubuntu.com/ubuntu/dists/dists/gutsy-backports/universe/i18n/Translation-en_US.bz2:) Could not resolve 'us.archive.ubuntu.com'
[http://us.archive.ubuntu.com/ubuntu/dists/dists/gutsy-backports/multiverse/i18n/Translation-en_US.bz2:](http://us.archive.ubuntu.com/ubuntu/dists/dists/gutsy-backports/multiverse/i18n/Translation-en_US.bz2:) Could not resolve 'us.archive.ubuntu.com'
[http://archive.canonical.com/ubuntu/dists/gutsy/Release.gpg:](http://archive.canonical.com/ubuntu/dists/gutsy/Release.gpg:) Could not resolve 'archive.canonical.com'
[http://archive.canonical.com/ubuntu/dists/gutsy/partner/i18n/Translation-en_US.bz2:](http://archive.canonical.com/ubuntu/dists/gutsy/partner/i18n/Translation-en_US.bz2:) Could not resolve 'archive.canonical.com'
[http://us.archive.ubuntu.com/ubuntu/dists/dists/gutsy-security/Release.gpg:](http://us.archive.ubuntu.com/ubuntu/dists/dists/gutsy-security/Release.gpg:) Could not resolve 'us.archive.ubuntu.com'
[http://us.archive.ubuntu.com/ubuntu/dists/dists/gutsy-security/main/i18n/Translation-en_US.bz2:](http://us.archive.ubuntu.com/ubuntu/dists/dists/gutsy-security/main/i18n/Translation-en_US.bz2:) Could not resolve 'us.archive.ubuntu.com'
[http://us.archive.ubuntu.com/ubuntu/dists/dists/gutsy-security/restricted/i18n/Translation-en_US.bz2:](http://us.archive.ubuntu.com/ubuntu/dists/dists/gutsy-security/restricted/i18n/Translation-en_US.bz2:) Could not resolve 'us.archive.ubuntu.com'
[http://us.archive.ubuntu.com/ubuntu/dists/dists/gutsy-security/universe/i18n/Translation-en_US.bz2:](http://us.archive.ubuntu.com/ubuntu/dists/dists/gutsy-security/universe/i18n/Translation-en_US.bz2:) Could not resolve 'us.archive.ubuntu.com'
[http://us.archive.ubuntu.com/ubuntu/dists/dists/gutsy-security/multiverse/i18n/Translation-en_US.bz2:](http://us.archive.ubuntu.com/ubuntu/dists/dists/gutsy-security/multiverse/i18n/Translation-en_US.bz2:) Could not resolve 'us.archive.ubuntu.com'
[http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg:](http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg:) Could not resolve 'archive.ubuntu.com'
[http://archive.ubuntu.com/ubuntu/dists/dapper/universe/i18n/Translation-en_US.bz2:](http://archive.ubuntu.com/ubuntu/dists/dapper/universe/i18n/Translation-en_US.bz2:) Could not resolve 'archive.ubuntu.com'
[http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/i18n/Translation-en_US.bz2:](http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/i18n/Translation-en_US.bz2:) Could not resolve 'archive.ubuntu.com'
[http://archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz:) Could not resolve 'archive.ubuntu.com'
[http://archive.canonical.com/ubuntu/dists/gutsy/partner/binary-i386/Packages.gz:](http://archive.canonical.com/ubuntu/dists/gutsy/partner/binary-i386/Packages.gz:) Could not resolve 'archive.canonical.com'
[http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz:) Could not resolve 'archive.ubuntu.com'
[http://archive.canonical.com/ubuntu/dists/gutsy/partner/source/Sources.gz:](http://archive.canonical.com/ubuntu/dists/gutsy/partner/source/Sources.gz:) Could not resolve 'archive.canonical.com'
[http://archive.ubuntu.com/ubuntu/dists/dapper/universe/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper/universe/source/Sources.gz:) Could not resolve 'archive.ubuntu.com'
[http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/source/Sources.gz:) Could not resolve 'archive.ubuntu.com'
[http://us.archive.ubuntu.com/ubuntu/dists/dists/gutsy/main/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/dists/gutsy/main/binary-i386/Packages.gz:) Could not resolve 'us.archive.ubuntu.com'
[http://us.archive.ubuntu.com/ubuntu/dists/dists/gutsy/restricted/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/dists/gutsy/restricted/binary-i386/Packages.gz:) Could not resolve 'us.archive.ubuntu.com'
[http://us.archive.ubuntu.com/ubuntu/dists/dists/gutsy/main/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/dists/gutsy/main/source/Sources.gz:) Could not resolve 'us.archive.ubuntu.com'
[http://us.archive.ubuntu.com/ubuntu/dists/dists/gutsy/restricted/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/dists/gutsy/restricted/source/Sources.gz:) Could not resolve 'us.archive.ubuntu.com'
[http://us.archive.ubuntu.com/ubuntu/dists/dists/gutsy/universe/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/dists/gutsy/universe/binary-i386/Packages.gz:) Could not resolve 'us.archive.ubuntu.com'
[http://us.archive.ubuntu.com/ubuntu/dists/dists/gutsy/universe/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/dists/gutsy/universe/source/Sources.gz:) Could not resolve 'us.archive.ubuntu.com'
[http://us.archive.ubuntu.com/ubuntu/dists/dists/gutsy/multiverse/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/dists/gutsy/multiverse/binary-i386/Packages.gz:) Could not resolve 'us.archive.ubuntu.com'
[http://us.archive.ubuntu.com/ubuntu/dists/dists/gutsy/multiverse/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/dists/gutsy/multiverse/source/Sources.gz:) Could not resolve 'us.archive.ubuntu.com'
[http://us.archive.ubuntu.com/ubuntu/dists/dists/gutsy-updates/main/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/dists/gutsy-updates/main/binary-i386/Packages.gz:) Could not resolve 'us.archive.ubuntu.com'
[http://us.archive.ubuntu.com/ubuntu/dists/dists/gutsy-updates/restricted/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/dists/gutsy-updates/restricted/binary-i386/Packages.gz:) Could not resolve 'us.archive.ubuntu.com'
[http://us.archive.ubuntu.com/ubuntu/dists/dists/gutsy-updates/main/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/dists/gutsy-updates/main/source/Sources.gz:) Could not resolve 'us.archive.ubuntu.com'
[http://us.archive.ubuntu.com/ubuntu/dists/dists/gutsy-updates/restricted/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/dists/gutsy-updates/restricted/source/Sources.gz:) Could not resolve 'us.archive.ubuntu.com'
[http://us.archive.ubuntu.com/ubuntu/dists/dists/gutsy-updates/universe/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/dists/gutsy-updates/universe/binary-i386/Packages.gz:) Could not resolve 'us.archive.ubuntu.com'
[http://us.archive.ubuntu.com/ubuntu/dists/dists/gutsy-updates/universe/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/dists/gutsy-updates/universe/source/Sources.gz:) Could not resolve 'us.archive.ubuntu.com'
[http://us.archive.ubuntu.com/ubuntu/dists/dists/gutsy-updates/multiverse/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/dists/gutsy-updates/multiverse/binary-i386/Packages.gz:) Could not resolve 'us.archive.ubuntu.com'
[http://us.archive.ubuntu.com/ubuntu/dists/dists/gutsy-updates/multiverse/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/dists/gutsy-updates/multiverse/source/Sources.gz:) Could not resolve 'us.archive.ubuntu.com'
[http://us.archive.ubuntu.com/ubuntu/dists/dists/gutsy-backports/main/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/dists/gutsy-backports/main/binary-i386/Packages.gz:) Could not resolve 'us.archive.ubuntu.com'
[http://us.archive.ubuntu.com/ubuntu/dists/dists/gutsy-backports/restricted/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/dists/gutsy-backports/restricted/binary-i386/Packages.gz:) Could not resolve 'us.archive.ubuntu.com'
[http://us.archive.ubuntu.com/ubuntu/dists/dists/gutsy-backports/universe/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/dists/gutsy-backports/universe/binary-i386/Packages.gz:) Could not resolve 'us.archive.ubuntu.com'
[http://us.archive.ubuntu.com/ubuntu/dists/dists/gutsy-backports/multiverse/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/dists/gutsy-backports/multiverse/binary-i386/Packages.gz:) Could not resolve 'us.archive.ubuntu.com'
[http://us.archive.ubuntu.com/ubuntu/dists/dists/gutsy-backports/main/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/dists/gutsy-backports/main/source/Sources.gz:) Could not resolve 'us.archive.ubuntu.com'
[http://us.archive.ubuntu.com/ubuntu/dists/dists/gutsy-backports/restricted/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/dists/gutsy-backports/restricted/source/Sources.gz:) Could not resolve 'us.archive.ubuntu.com'
[http://us.archive.ubuntu.com/ubuntu/dists/dists/gutsy-backports/universe/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/dists/gutsy-backports/universe/source/Sources.gz:) Could not resolve 'us.archive.ubuntu.com'
[http://us.archive.ubuntu.com/ubuntu/dists/dists/gutsy-backports/multiverse/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/dists/gutsy-backports/multiverse/source/Sources.gz:) Could not resolve 'us.archive.ubuntu.com'
[http://us.archive.ubuntu.com/ubuntu/dists/dists/gutsy-security/main/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/dists/gutsy-security/main/binary-i386/Packages)
.gz: Could not resolve 'us.archive.ubuntu.com'


A lot issues.

---


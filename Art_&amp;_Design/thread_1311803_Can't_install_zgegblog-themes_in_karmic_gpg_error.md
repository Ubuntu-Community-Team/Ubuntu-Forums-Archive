---
title: "Can't install zgegblog-themes in karmic gpg error"
date: 2009-11-02
forum: Art &amp; Design
---

### Post by shafi on 2009-11-02
Hi,
I wanna install some cool thems from ubuntugeek website [http://www.ubuntugeek.com/nice-themes-for-ubuntu-9-10-karmic-users.html](http://www.ubuntugeek.com/nice-themes-for-ubuntu-9-10-karmic-users.html), 
but when I am going to add the gpg for installing zgegblog-themes I get the following error:
```

~$ sudo add-apt-repository ppa:bisigi

Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv 1781BD45C4C3275A34BB6AEC6E871C4A881574DE
gpg: requesting key 881574DE from hkp server keyserver.ubuntu.com
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error


```

```

~$ gpg --keyserver hkp://keyserver.ubuntu.com:11371 --recv-key 881574DE && gpg -a --export 881574DE | sudo apt-key add -

gpg: WARNING: unsafe permissions on configuration file `/home/shafi/.gnupg/gpg.conf'
gpg: WARNING: unsafe enclosing directory permissions on configuration file `/home/shafi/.gnupg/gpg.conf'
gpg: external program calls are disabled due to unsafe options file permissions
gpg: keyserver communications error: general error
gpg: keyserver receive failed: general error

```
can some one help me in this regard? thanks.

---

### Post by sisco311 on 2009-11-02
The keyserver is slow. This is the public key:
```
-----BEGIN PGP PUBLIC KEY BLOCK-----
Version: SKS 1.0.10

mI0ESbZqaAEEAK68aXUddzAxUmMkB/zESfiK1laJ6OC0yrjfu8hDkHPrO4UgiT+7LU+49qBz
tQGJwaS/S2Y/Ya5mATPq08x7CTz35BnpKoaNDr5zcKeybKMYiY+LdKZRfJQqJ6IhIzINzb41
Lb7R9eJyXfYpRkXdWNbHrHvm1Z9fZuubnTjH1mMPABEBAAG0GExhdW5jaHBhZCBQUEEgZm9y
IEJpc2lnaYi2BBMBAgAgBQJJtmpoAhsDBgsJCAcDAgQVAggDBBYCAwECHgECF4AACgkQbocc
SogVdN6PdQQAldkJkwZsJb6cRS2emDzImh3+p4lStpOHmvLsAE68oGmoiTGmDHOePP+UvfJh
lYp2kmg5M/P8d3hLfg4cXNCWJnTCfYAs42/A/1vymoEfhwo21PkiFhXM+6pfFULDlAMyrjeI
QZ+NPDxvUsdpik5eBlU1jE2YTKxzlEkaVHxwFUw=
=MFvp
-----END PGP PUBLIC KEY BLOCK-----
```

I was able to download it from: [http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0x6E871C4A881574DE]("http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0x6E871C4A881574DE")

copy/paste the key in a file:
```
nano bisigi.key
```
press Ctrl+x, y, Enter to save the file and exit.

add the key
```
sudo apt-key add bisigi.key
```

---

### Post by shafi on 2009-11-03
Thanks,
worked greate !

---


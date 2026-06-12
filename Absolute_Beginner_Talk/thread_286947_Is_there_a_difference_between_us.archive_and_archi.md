---
title: "Is there a difference between us.archive and archive"
date: 2006-10-28
forum: Absolute Beginner Talk
---

### Post by kent41 on 2006-10-28
Is there a difference between us.archive and archive as to the download servers used to update ?

Or are they the same server

---

### Post by dbott67 on 2006-10-28
I don't think so... the US archives are just a mirror of the main archives.  Each country / region seems to have their own set of mirrors to use so they don't totally swamp the main archives.

The only thing I'm unsure about is the propogation of updates (i.e. how long before the mirrored sites are synched to the main site.

-Dave

---

### Post by kent41 on 2006-10-28
> **dbott67 said:**
> I don't think so... the US archives are just a mirror of the main archives.  Each country / region seems to have their own set of mirrors to use so they don't totally swamp the main archives.

The only thing I'm unsure about is the propogation of updates (i.e. how long before the mirrored sites are synched to the main site.

-Dave

Thanks the reason I ask was that on one computer I can update using Breezy 5.10 which updates using archive but can not update using edgy 6.10 using us.archive

---

### Post by kent41 on 2006-10-28
UPDATE

I found that I can ping **archive.ubuntu.com** but I can not ping **us.archive.ubuntu.com   **  

any ideas ?

---

### Post by dbott67 on 2006-10-28
Well, it could be swamped right now, as everyone trying to get Edgy.  There is a sources.list generator here:

[http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)

It allows you to create a new sources.list file by selecting which country & repos you want to use.  The only thing is that it does not have the edgy repos enabled yet (but you could just replace every instance of **dapper** with **edgy** & you should be okay.
```
# Automatically generated sources.list
# http://www.ubuntulinux.nl/source-o-matic
#
# If you get errors about missing keys, lookup the key in this file
# and run these commands (replace KEY with the key number)
#
# gpg --keyserver subkeys.pgp.net --recv KEY
# gpg --export --armor KEY | sudo apt-key add -

# Ubuntu supported packages (packages, GPG key: 437D05B5)
deb http://ca.archive.ubuntu.com/ubuntu dapper main restricted
deb http://ca.archive.ubuntu.com/ubuntu dapper-updates main restricted
deb http://security.ubuntu.com/ubuntu dapper-security main restricted

# Ubuntu supported packages (sources, GPG key: 437D05B5)
deb-src http://ca.archive.ubuntu.com/ubuntu dapper main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu dapper-updates main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted

# Ubuntu community supported packages (packages, GPG key: 437D05B5)
deb http://ca.archive.ubuntu.com/ubuntu dapper universe multiverse
deb http://ca.archive.ubuntu.com/ubuntu dapper-updates universe multiverse
deb http://security.ubuntu.com/ubuntu dapper-security universe multiverse

# Ubuntu community supported packages (sources, GPG key: 437D05B5)
deb-src http://ca.archive.ubuntu.com/ubuntu dapper universe multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu dapper-updates universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security universe multiverse
```

Try changing the county code from US to CA (=Canada) or any of the other 2-digit country codes.
-Dave

---

### Post by kent41 on 2006-10-28
> **dbott67 said:**
> Well, it could be swamped right now, as everyone trying to get Edgy.  There is a sources.list generator here:

[http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)

It allows you to create a new sources.list file by selecting which country & repos you want to use.  The only thing is that it does not have the edgy repos enabled yet (but you could just replace every instance of **dapper** with **edgy** & you should be okay.
```
# Automatically generated sources.list
# http://www.ubuntulinux.nl/source-o-matic
#
# If you get errors about missing keys, lookup the key in this file
# and run these commands (replace KEY with the key number)
#
# gpg --keyserver subkeys.pgp.net --recv KEY
# gpg --export --armor KEY | sudo apt-key add -

# Ubuntu supported packages (packages, GPG key: 437D05B5)
deb http://ca.archive.ubuntu.com/ubuntu dapper main restricted
deb http://ca.archive.ubuntu.com/ubuntu dapper-updates main restricted
deb http://security.ubuntu.com/ubuntu dapper-security main restricted

# Ubuntu supported packages (sources, GPG key: 437D05B5)
deb-src http://ca.archive.ubuntu.com/ubuntu dapper main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu dapper-updates main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted

# Ubuntu community supported packages (packages, GPG key: 437D05B5)
deb http://ca.archive.ubuntu.com/ubuntu dapper universe multiverse
deb http://ca.archive.ubuntu.com/ubuntu dapper-updates universe multiverse
deb http://security.ubuntu.com/ubuntu dapper-security universe multiverse

# Ubuntu community supported packages (sources, GPG key: 437D05B5)
deb-src http://ca.archive.ubuntu.com/ubuntu dapper universe multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu dapper-updates universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security universe multiverse
```
-Dave


Thanks Dave I try it later I have to go to an appointment now

---


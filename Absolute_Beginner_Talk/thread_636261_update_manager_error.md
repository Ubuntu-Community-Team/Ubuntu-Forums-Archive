---
title: "update manager error"
date: 2007-12-09
forum: Absolute Beginner Talk
---

### Post by bratliff on 2007-12-09
Is there a reason the update manager does not connect to the OPera update?

bratliff

---

### Post by nikoPSK on 2007-12-09
would you try it again?

---

### Post by jonward690 on 2007-12-09
I have had problems where the update would not work in the gui and I just re ran it in the command line with no problems.

---

### Post by nikoPSK on 2007-12-09
just do that then:

```
sudo apt-get update
```
and
```
sudo apt-get upgrade
```

---

### Post by bratliff on 2007-12-10
example of sudo apt-get update errors

bratliff


root@bob-desktop2:~# sudo apt-get update
Err [http://pa.archive.ubuntu.com](http://pa.archive.ubuntu.com) gutsy Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection ref
used)
Err [http://pa.archive.ubuntu.com](http://pa.archive.ubuntu.com) gutsy/main Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection ref
used)
Err [http://pa.archive.ubuntu.com](http://pa.archive.ubuntu.com) gutsy/restricted Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection ref
used)
Err [http://pa.archive.ubuntu.com](http://pa.archive.ubuntu.com) gutsy/universe Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection ref
used)
Err [http://pa.archive.ubuntu.com](http://pa.archive.ubuntu.com) gutsy/multiverse Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection ref
used)
Err [http://pa.archive.ubuntu.com](http://pa.archive.ubuntu.com) gutsy-updates Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection ref
used)
Err [http://pa.archive.ubuntu.com](http://pa.archive.ubuntu.com) gutsy-updates/main Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection ref
used)
Err [http://pa.archive.ubuntu.com](http://pa.archive.ubuntu.com) gutsy-updates/restricted Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection ref
used)
Err [http://pa.archive.ubuntu.com](http://pa.archive.ubuntu.com) gutsy-updates/universe Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection ref
used)
Err [http://pa.archive.ubuntu.com](http://pa.archive.ubuntu.com) gutsy-updates/multiverse Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection ref
used)
Err [http://www.linuxmint.com](http://www.linuxmint.com) romeo/ Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection ref
used)
Err [http://www.linuxmint.com](http://www.linuxmint.com) romeo/ Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection ref
used)
Err [http://www.remastersys.klikit.org](http://www.remastersys.klikit.org) remastersys/ Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection ref
used)
Err [http://www.remastersys.klikit.org](http://www.remastersys.klikit.org) remastersys/ Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection ref
used)
Err [http://archive.canonical.com](http://archive.canonical.com) gutsy Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection ref
used)
Err [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection ref
used)
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection ref
used)
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection ref
used)
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection ref
used)
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection ref
used)
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection ref
used)
Err [http://ftp.osuosl.org](http://ftp.osuosl.org) gutsy/ Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection ref
used)
Err [http://ftp.osuosl.org](http://ftp.osuosl.org) gutsy/ Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection ref
used)
Err [http://blognux.free.fr](http://blognux.free.fr) unstable Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection ref
used)
Err [http://blognux.free.fr](http://blognux.free.fr) unstable/main Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection ref
used)
Err [http://pa.archive.ubuntu.com](http://pa.archive.ubuntu.com) gutsy-security Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection ref
used)
Err [http://pa.archive.ubuntu.com](http://pa.archive.ubuntu.com) gutsy-security/main Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection ref
used)
Err [http://pa.archive.ubuntu.com](http://pa.archive.ubuntu.com) gutsy-security/restricted Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection ref
used)
Err [http://pa.archive.ubuntu.com](http://pa.archive.ubuntu.com) gutsy-security/universe Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection ref
used)
Err [http://pa.archive.ubuntu.com](http://pa.archive.ubuntu.com) gutsy-security/multiverse Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection ref
used)
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy Release.g
pg
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Tran
slation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricte
d Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy Release
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Pack
ages
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricte
d Packages
Err cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Pack
ages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update can
not be used to add new CD-ROMs
Err cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricte
d Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update can
not be used to add new CD-ROMs
Ign file: apt-build Release.gpg
Ign file: apt-build/main Translation-en_US
Get:1 file: apt-build Release [89B]
Ign file: apt-build/main Packages
Failed to fetch [http://pa.archive.ubuntu.com/ubuntu/dists/gutsy/Release.gpg](http://pa.archive.ubuntu.com/ubuntu/dists/gutsy/Release.gpg)  Cou
ld not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://pa.archive.ubuntu.com/ubuntu/dists/gutsy/main/i18n/Transl](http://pa.archive.ubuntu.com/ubuntu/dists/gutsy/main/i18n/Transl)
ation-en_US.bz2  Could not connect to localhost:4001 (127.0.0.1). - connect (111
 Connection refused)
Failed to fetch [http://pa.archive.ubuntu.com/ubuntu/dists/gutsy/restricted/i18n/](http://pa.archive.ubuntu.com/ubuntu/dists/gutsy/restricted/i18n/)
Translation-en_US.bz2  Could not connect to localhost:4001 (127.0.0.1). - connec
t (111 Connection refused)
Failed to fetch [http://pa.archive.ubuntu.com/ubuntu/dists/gutsy/universe/i18n/Tr](http://pa.archive.ubuntu.com/ubuntu/dists/gutsy/universe/i18n/Tr)
anslation-en_US.bz2  Could not connect to localhost:4001 (127.0.0.1). - connect
(111 Connection refused)
Failed to fetch [http://pa.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/i18n/](http://pa.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/i18n/)
Translation-en_US.bz2  Could not connect to localhost:4001 (127.0.0.1). - connec
t (111 Connection refused)
Failed to fetch [http://pa.archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release](http://pa.archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release).
gpg  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection
refused)
Failed to fetch [http://pa.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/i18](http://pa.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/i18)
n/Translation-en_US.bz2  Could not connect to localhost:4001 (127.0.0.1). - conn
ect (111 Connection refused)
Failed to fetch [http://pa.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restrict](http://pa.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restrict)
ed/i18n/Translation-en_US.bz2  Could not connect to localhost:4001 (127.0.0.1).
- connect (111 Connection refused)
Failed to fetch [http://pa.archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe](http://pa.archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe)
/i18n/Translation-en_US.bz2  Could not connect to localhost:4001 (127.0.0.1). -
connect (111 Connection refused)
Failed to fetch [http://pa.archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiver](http://pa.archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiver)
se/i18n/Translation-en_US.bz2  Could not connect to localhost:4001 (127.0.0.1).
- connect (111 Connection refused)
Failed to fetch [http://archive.canonical.com/ubuntu/dists/gutsy/Release.gpg](http://archive.canonical.com/ubuntu/dists/gutsy/Release.gpg)  Cou
ld not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://archive.canonical.com/ubuntu/dists/gutsy/partner/i18n/Tra](http://archive.canonical.com/ubuntu/dists/gutsy/partner/i18n/Tra)
nslation-en_US.bz2  Could not connect to localhost:4001 (127.0.0.1). - connect (
111 Connection refused)
Failed to fetch [http://pa.archive.ubuntu.com/ubuntu/dists/gutsy-security/Release](http://pa.archive.ubuntu.com/ubuntu/dists/gutsy-security/Release)
.gpg  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection
 refused)
Failed to fetch [http://pa.archive.ubuntu.com/ubuntu/dists/gutsy-security/main/i1](http://pa.archive.ubuntu.com/ubuntu/dists/gutsy-security/main/i1)
8n/Translation-en_US.bz2  Could not connect to localhost:4001 (127.0.0.1). - con
nect (111 Connection refused)
Failed to fetch [http://pa.archive.ubuntu.com/ubuntu/dists/gutsy-security/restric](http://pa.archive.ubuntu.com/ubuntu/dists/gutsy-security/restric)
ted/i18n/Translation-en_US.bz2  Could not connect to localhost:4001 (127.0.0.1).
 - connect (111 Connection refused)
Failed to fetch [http://pa.archive.ubuntu.com/ubuntu/dists/gutsy-security/univers](http://pa.archive.ubuntu.com/ubuntu/dists/gutsy-security/univers)
e/i18n/Translation-en_US.bz2  Could not connect to localhost:4001 (127.0.0.1). -
 connect (111 Connection refused)
Failed to fetch [http://pa.archive.ubuntu.com/ubuntu/dists/gutsy-security/multive](http://pa.archive.ubuntu.com/ubuntu/dists/gutsy-security/multive)
rse/i18n/Translation-en_US.bz2  Could not connect to localhost:4001 (127.0.0.1).
 - connect (111 Connection refused)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/Release.g](http://security.ubuntu.com/ubuntu/dists/gutsy-security/Release.g)
pg  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection r
efused)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/i18n](http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/i18n)
/Translation-en_US.bz2  Could not connect to localhost:4001 (127.0.0.1). - conne
ct (111 Connection refused)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricte](http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricte)
d/i18n/Translation-en_US.bz2  Could not connect to localhost:4001 (127.0.0.1). -
 connect (111 Connection refused)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/](http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/)
i18n/Translation-en_US.bz2  Could not connect to localhost:4001 (127.0.0.1). - c
onnect (111 Connection refused)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/multivers](http://security.ubuntu.com/ubuntu/dists/gutsy-security/multivers)
e/i18n/Translation-en_US.bz2  Could not connect to localhost:4001 (127.0.0.1). -
 connect (111 Connection refused)
Failed to fetch [http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/u](http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/u)
buntu/gutsy/Release.gpg  Could not connect to localhost:4001 (127.0.0.1). - conn
ect (111 Connection refused)
Failed to fetch [http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/u](http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/u)
buntu/gutsy/en_US.bz2  Could not connect to localhost:4001 (127.0.0.1). - connec
t (111 Connection refused)
Failed to fetch [http://blognux.free.fr/debian/dists/unstable/Release.gpg](http://blognux.free.fr/debian/dists/unstable/Release.gpg)  Could
not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://blognux.free.fr/debian/dists/unstable/main/i18n/Translati](http://blognux.free.fr/debian/dists/unstable/main/i18n/Translati)                                                                            on-en_US.bz2  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Co                                                                            nnection refused)
Failed to fetch [http://www.linuxmint.com/repository/romeo/Release.gpg](http://www.linuxmint.com/repository/romeo/Release.gpg)  Could not                                                                             connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://www.linuxmint.com/repository/romeo/en_US.bz2](http://www.linuxmint.com/repository/romeo/en_US.bz2)  Could not c                                                                            onnect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://www.remastersys.klikit.org/repository/remastersys/Release](http://www.remastersys.klikit.org/repository/remastersys/Release)                                                                            .gpg  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection                                                                             refused)
Failed to fetch [http://www.remastersys.klikit.org/repository/remastersys/en_US.b](http://www.remastersys.klikit.org/repository/remastersys/en_US.b)                                                                            z2  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection r                                                                            efused)
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/dis                                                                            ts/gutsy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM                                                                             recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/dis                                                                            ts/gutsy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this C                                                                            D-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used                                                                             instead.
root@bob-desktop2:~#
sudo apt-get update

---

### Post by bratliff on 2007-12-10
I have tried several times. Same result.

bratliff

> **nikoPSK said:**
> would you try it again?

---

### Post by nikoPSK on 2007-12-10
well, you could possibly have broken repos or disabled some? Make sure all repos (universe, multiverse etc...) are enabled.

---

### Post by bratliff on 2007-12-10
THanks, but not the problem.


What's with the cannot connect to 127.0.0.1?

bratliff

---

### Post by nikoPSK on 2007-12-10
it's an ip address. Look it up in google. I cannot help anymore as this is beyond me now.

---

### Post by bratliff on 2007-12-10
LOL, Right it's your own loopback address.
bratliff


> **nikoPSK said:**
> it's an ip address. Look it up in google. I cannot help anymore as this is beyond me now.

---

### Post by nikoPSK on 2007-12-10
:p, also put your terminal output in code tags.

```
ExampleExampleExampleExampleExampleExampleExampleExampleExampleExampleExampleExampleExampleExample
```

---

### Post by bratliff on 2007-12-11
sudo apt-get upgrade give me this:


root@bob-desktop2:~# sudo apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be upgraded:
  opera
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 5657kB of archives.
After unpacking 49.2kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  opera
Install these packages without verification [y/N]? y
Err [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner opera 9.24-20071015.6gutsy1
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://archive.canonical.com/ubuntu/pool/partner/o/opera/opera_9.24-20071015.6gutsy1_i386.deb](http://archive.canonical.com/ubuntu/pool/partner/o/opera/opera_9.24-20071015.6gutsy1_i386.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
root@bob-desktop2:~#

bratliff


> **nikoPSK said:**
> just do that then:

```
sudo apt-get update
```
and
```
sudo apt-get upgrade
```

---


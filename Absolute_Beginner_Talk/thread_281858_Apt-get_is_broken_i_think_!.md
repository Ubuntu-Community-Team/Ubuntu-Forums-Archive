---
title: "Apt-get is broken i think !"
date: 2006-10-21
forum: Absolute Beginner Talk
---

### Post by D_frag on 2006-10-21
Well i tries to install gammu , wammu and all their stuff hoping to be able to not havw to go to windows to use the nokia pc suite and whenever i tried to install a lib or dependcy i got a problem i tried looking for the   packages in synaptic but never found them so i downloaded them my self and used the debian packages to install them .deb files tried tzdata i got a weird error like it was installed or somthing but when i tried to install a lib that depended on it i got missing dependency and now i think apt-get update is broken ..not working cuz i have to resolve the problems and when i ran apt-get install -f i got this any help 

```
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... failed.
The following packages have unmet dependencies:
  gammu: Depends: libgammu0 (< 1.08.00-99) but it is not installable
         Depends: libgammu0 (>= 1.08.00) but it is not installable
         Depends: libmysqlclient15off (>= 5.0.24-2) but 5.0.22-0ubuntu6.06.2 is installed
  libc6: Depends: tzdata but it is not installable
  libc6-dev: Depends: libc6 (= 2.3.6-0ubuntu20) but 2.3.6.ds1-6 is installed
  libc6-i386: Depends: libc6 (= 2.3.6-0ubuntu20) but 2.3.6.ds1-6 is installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies
```

---

### Post by raul_ on 2006-10-21
Lol. it's not broken. try to search for those packages in synaptic and install them both (if they are available of course)

---

### Post by Sef on 2006-10-21
To install them, you may need to enable the [repositories]("https://help.ubuntu.com/community/Repositories/Ubuntu").

---

### Post by D_frag on 2006-10-22
the repos are enabled and those packages are not available on synaptic !  so what should i do ?

---


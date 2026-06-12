---
title: "Downloading packages on another machine"
date: 2005-08-21
forum: Apple PPC Users
---

### Post by jameskl on 2005-08-21
Is it possible to download packages on a machine running os x then transfer + install them in Ubuntu?

Yes somebody blew their traffic on downloading the installer and updates ;)

Thanks,
James.

---

### Post by nad on 2005-08-21
Certainly. Use packages.ubuntu.com to search for and download any packages you wish or just download the debs directly from archive.ubuntu.com .

Put them in a handy place, say, /var/apt/cache/archives and use dpkg -i package_name to install them. They will still be managed this way.

---


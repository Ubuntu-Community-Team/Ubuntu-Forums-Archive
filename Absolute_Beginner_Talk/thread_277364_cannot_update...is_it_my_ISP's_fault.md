---
title: "cannot update...is it my ISP's fault?"
date: 2006-10-14
forum: Absolute Beginner Talk
---

### Post by turo on 2006-10-14
My internet access is provided by my apartment complex.  A few days ago, they set up a firewall to prevent residents from accessing illegal file sharing services (kazaa, morpheus, etc).  Since then, I have not been able to run apt-get update on my pc, it always gives me a "forbidden" followed by a "failed to fetch http:..." errors.  Here is what I mean...

```

/etc/apt$ sudo apt-get update
Ign http://us.archive.ubuntu.com dapper Release.gpg
Ign http://us.archive.ubuntu.com dapper-updates Release.gpg
Ign http://us.archive.ubuntu.com dapper Release
Ign http://us.archive.ubuntu.com dapper-updates Release
Ign http://us.archive.ubuntu.com dapper/main Packages
Ign http://us.archive.ubuntu.com dapper/restricted Packages
Ign http://us.archive.ubuntu.com dapper/main Sources
Ign http://us.archive.ubuntu.com dapper/restricted Sources
Ign http://us.archive.ubuntu.com dapper-updates/main Packages
Ign http://us.archive.ubuntu.com dapper-updates/restricted Packages
Ign http://us.archive.ubuntu.com dapper-updates/main Sources
Ign http://us.archive.ubuntu.com dapper-updates/restricted Sources
Err http://us.archive.ubuntu.com dapper/main Packages
  403 Forbidden [IP: 146.137.96.15 80]
Err http://us.archive.ubuntu.com dapper/restricted Packages
  403 Forbidden [IP: 146.137.96.15 80]
Err http://us.archive.ubuntu.com dapper/main Sources
  403 Forbidden [IP: 146.137.96.15 80]
Err http://us.archive.ubuntu.com dapper/restricted Sources
  403 Forbidden [IP: 146.137.96.15 80]
Err http://us.archive.ubuntu.com dapper-updates/main Packages
  403 Forbidden [IP: 146.137.96.15 80]
Err http://us.archive.ubuntu.com dapper-updates/restricted Packages
  403 Forbidden [IP: 146.137.96.15 80]
Err http://us.archive.ubuntu.com dapper-updates/main Sources
  403 Forbidden [IP: 146.137.96.15 80]
Err http://us.archive.ubuntu.com dapper-updates/restricted Sources
  403 Forbidden [IP: 146.137.96.15 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz  403 Forbidden [IP: 146.137.96.15 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz  403 Forbidden [IP: 146.137.96.15 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz  403 Forbidden [IP: 146.137.96.15 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources.gz  403 Forbidden [IP: 146.137.96.15 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz  403 Forbidden [IP: 146.137.96.15 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz  403 Forbidden [IP: 146.137.96.15 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz  403 Forbidden [IP: 146.137.96.15 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/source/Sources.gz  403 Forbidden [IP: 146.137.96.15 80]
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

```

I also cannot download anything using Adept.  I tried using the original sources.list file, as well as switching every address from http to ftp, but nothing seems to work.  I have a feeling that it has to be the firewall set up by my complex, because everything was working fine until then.  Is there any way of getting around this?  Could the problem be something else?

---

### Post by Kateikyoushi on 2006-10-14
I also can't open those addresses so they might be down or even obsolate ?

Try to get a new list from [here]("http://www.psychocats.net/ubuntu/sources").

---

### Post by turo on 2006-10-14
That solved the problem!  Not sure, but I think they might have just been obsolete.  Either way it works now, so thanks! :)

---


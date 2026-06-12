---
title: "Cannot reload amsn"
date: 2008-01-09
forum: Absolute Beginner Talk
---

### Post by aja on 2008-01-09
Can someone please help??

I had amsn up and running, but I wanted to install the new version 0.97. Being new I figured I could just remove  the program using add / remove Then just reinstall it. Now when I try to reinstall amsn using add / remove I get this

[http://security.ubuntu.com/ubuntu/dists/gutsy-security/Release:](http://security.ubuntu.com/ubuntu/dists/gutsy-security/Release:) Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
[http://us.archive.ubuntu.com/ubuntu/dists/gutsy/Release:](http://us.archive.ubuntu.com/ubuntu/dists/gutsy/Release:) Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
[http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release:](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release:) Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)



When I try to load it from synaptic package manager it is not listed ???


Thanks

aja

---

### Post by mdpalow on 2008-01-09
Add emesene to your source list:

```
sudo gedit /etc/apt/sources.list
```

Paste this at the bottom of sources.list

```
deb http://apt.emesene.org/ ./
deb-src http://apt.emesene.org/ ./
```

Update your repository by entering:

```
sudo apt-get update
```

Now try and install emesene from Terminal again..

```
sudo apt-get install emesene
```

---

### Post by Sef on 2008-01-09
If you want amsn 0.97, then you will have to download it from [amsn]("http://www.amsn-project.net/linux-downloads.php") itself.  There is a [self-installing installer]("http://www.autopackage.org/docs/howto-install/") which is easy to use with the directions.  The repositories only have 0.96.

---

### Post by mdpalow on 2008-01-09
> **Sef said:**
> If you want amsn 0.97, then you will have to download it from [amsn]("http://www.amsn-project.net/linux-downloads.php") itself.  There is a [self-installing installer]("http://www.autopackage.org/docs/howto-install/") which is easy to use with the directions.  The repositories only have 0.96.

uh.... I just gave you instructions for downloading 1.0.

---


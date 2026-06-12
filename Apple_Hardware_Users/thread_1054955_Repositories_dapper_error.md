---
title: "Repositories dapper error"
date: 2009-01-30
forum: Apple Hardware Users
---

### Post by vector on 2009-01-30
Hi,
I followed a previous thread [http://ubuntuforums.org/showthread.php?t=970056&highlight=repository](http://ubuntuforums.org/showthread.php?t=970056&highlight=repository) in an attempt to get my old power pc (.6.06lts. powerbook G3 pismo) going again.
it has a bonobo failure when it boots whilst there is no network available.

Obviously the repos are old. and from what I can tell from the above post 
I have to change it all too. /etc/apt/sources.list
 ```
deb http://ports.ubuntu.com/ubuntu-ports/ dapper main restricted universe multiverse
deb http://ports.ubuntu.com/ubuntu-ports/ dapper-updates main restricted universe multiverse
deb http://ports.ubuntu.com/ubuntu-ports/ dapper-security main restricted universe
deb http://ports.ubuntu.com/ubuntu-ports/ dapper-security main restricted  multiverse universe

```

however if get some Ign and some errors.
sudo apt-get update
Get:1 [http://ports.ubuntu.com](http://ports.ubuntu.com) dapper Release.gpg [189B]
Get:2 [http://ports.ubuntu.com](http://ports.ubuntu.com) dapper-updates Release.gpg [189B]
Get:3 [http://ports.ubuntu.com](http://ports.ubuntu.com) dapper-security Release.gpg [189B]
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) dapper Release
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) dapper-updates Release
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) dapper-security Release
Ign [http://ports.ubuntu.com](http://ports.ubuntu.com) dapper/main Packages
Ign [http://ports.ubuntu.com](http://ports.ubuntu.com) dapper-updates/main Packages
Ign [http://ports.ubuntu.com](http://ports.ubuntu.com) dapper-updates/restricted Packages
Ign [http://ports.ubuntu.com](http://ports.ubuntu.com) dapper-updates/universe Packages
Ign [http://ports.ubuntu.com](http://ports.ubuntu.com) dapper-updates/multiverse Packages
Ign [http://ports.ubuntu.com](http://ports.ubuntu.com) dapper-security/main Packages
Ign [http://ports.ubuntu.com](http://ports.ubuntu.com) dapper-security/restricted Packages
Ign [http://ports.ubuntu.com](http://ports.ubuntu.com) dapper-security/universe Packages
Ign [http://ports.ubuntu.com](http://ports.ubuntu.com) dapper-security/main Packages
Ign [http://ports.ubuntu.com](http://ports.ubuntu.com) dapper-security/restricted Packages
Ign [http://ports.ubuntu.com](http://ports.ubuntu.com) dapper-security/universe Packages
Ign [http://ports.ubuntu.com](http://ports.ubuntu.com) dapper-security/multiverse Packages
Err [http://ports.ubuntu.com](http://ports.ubuntu.com) dapper/main Packages
  404 Not Found
Err [http://ports.ubuntu.com](http://ports.ubuntu.com) dapper-updates/main Packages
  404 Not Found
Err [http://ports.ubuntu.com](http://ports.ubuntu.com) dapper-updates/restricted Packages
  404 Not Found
Err [http://ports.ubuntu.com](http://ports.ubuntu.com) dapper-updates/universe Packages
  404 Not Found
Err [http://ports.ubuntu.com](http://ports.ubuntu.com) dapper-updates/multiverse Packages
  404 Not Found
Err [http://ports.ubuntu.com](http://ports.ubuntu.com) dapper-security/main Packages
  404 Not Found
Err [http://ports.ubuntu.com](http://ports.ubuntu.com) dapper-security/restricted Packages
  404 Not Found
Err [http://ports.ubuntu.com](http://ports.ubuntu.com) dapper-security/universe Packages
  404 Not Found
Err [http://ports.ubuntu.com](http://ports.ubuntu.com) dapper-security/main Packages
  404 Not Found
Err [http://ports.ubuntu.com](http://ports.ubuntu.com) dapper-security/restricted Packages
  404 Not Found
Err [http://ports.ubuntu.com](http://ports.ubuntu.com) dapper-security/universe Packages
  404 Not Found
Err [http://ports.ubuntu.com](http://ports.ubuntu.com) dapper-security/multiverse Packages
  404 Not Found
Fetched 3B in 14s (0B/s)
Failed to fetch [http://ports.ubuntu.com/ubuntu-ports/dists/dapper/Release](http://ports.ubuntu.com/ubuntu-ports/dists/dapper/Release) Unable to find expected entry  restircted/binary-powerpc/Packages in Meta-index file (malformed Release file?)

---

### Post by cyberdork33 on 2009-01-30
I think there were some recent server issues. See here:
[http://ubuntuforums.org/showthread.php?t=1054874](http://ubuntuforums.org/showthread.php?t=1054874)

---

### Post by vector on 2009-01-30
Thanks Ill keep an eye on that thread to.
Im not sure its the same problem.
When i manually check the failed address...
 ```

Failed to fetch http://ports.ubuntu.com/ubuntu-ports...dapper/Release Unable to find expected entry restircted/binary-powerpc/Packages in Meta-index file (malformed Release file?)

```

**restircted/binary-powerpc**
its not in the sites directory tree

I also found reference to using 

deb [http://archive.ubuntu.com/ubuntu-ports/](http://archive.ubuntu.com/ubuntu-ports/) dapper main restricted universe multiverse


so I tried that but got similar results
```

Failed to fetch http://archive.ubuntu.com/ubuntu-ports/dists/dapper-security/multiverse/binary-powerpc/Packages.gz 404 Not Found [IP: 91.189.88.45 80]

```

looking on that url in the dir tree at least I can find  binary-powerpc/Packages. gz
why cant apt-get update find it?

---

### Post by jocko on 2009-01-31
> **vector said:**
> looking on that url in the dir tree at least I can find  binary-powerpc/Packages. gz
why cant apt-get update find it?

If you look more carefully you can see that there are only gutsy and hardy packages in that repo (at least I can only see 2.6.22 and 2.6.24 kernels for powerpc, dapper had 2.6.15).
I guess it's because the ppc version of ubuntu is just a port, so the ppc version of dapper did not have LTS status, which is why the repos does not contain dapper packages anymore... Just my guess...

Edit: I may have been wrong, apparently ppc was officially supported until 6.10, so I guess 6.06 ppc should have LTS status, which means the repos should be active until june...

---


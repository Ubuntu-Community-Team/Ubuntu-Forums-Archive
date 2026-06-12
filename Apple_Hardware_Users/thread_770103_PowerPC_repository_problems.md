---
title: "PowerPC repository problems?"
date: 2008-04-27
forum: Apple Hardware Users
---

### Post by DrivinWest on 2008-04-27
I'm relatively new to Linux and totally new to running it on PPC hardware.  I've got a PowerBook G4 1.5GHz with 1.25GB of RAM running Hardy.

While most things seems to be working well thus far, I've got some real problems with the default repository setup (actually I did enable the main, universe, multiverse, and restricted repositories, but I think the errors are all third-party repositories?  Maybe?).  Whenever I run Update Manager or Synaptic Package Manager I get the following errors:

> Failed to fetch [http://ports.ubuntu.com/ubuntu-ports/dists/hardy-security/main/source/Sources.gz](http://ports.ubuntu.com/ubuntu-ports/dists/hardy-security/main/source/Sources.gz)  404 Not Found
Failed to fetch [http://ports.ubuntu.com/ubuntu-ports/dists/hardy-security/restricted/source/Sources.gz](http://ports.ubuntu.com/ubuntu-ports/dists/hardy-security/restricted/source/Sources.gz)  404 Not Found
Failed to fetch [http://ports.ubuntu.com/ubuntu-ports/dists/hardy-security/universe/source/Sources.gz](http://ports.ubuntu.com/ubuntu-ports/dists/hardy-security/universe/source/Sources.gz)  404 Not Found
Failed to fetch [http://ports.ubuntu.com/ubuntu-ports/dists/hardy-security/multiverse/source/Sources.gz](http://ports.ubuntu.com/ubuntu-ports/dists/hardy-security/multiverse/source/Sources.gz)  404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/main/binary-powerpc/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy/main/binary-powerpc/Packages.gz)  404 Not Found [IP: 91.189.92.22 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-powerpc/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-powerpc/Packages.gz)  404 Not Found [IP: 91.189.92.22 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/restricted/binary-powerpc/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy/restricted/binary-powerpc/Packages.gz)  404 Not Found [IP: 91.189.92.22 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/binary-powerpc/Packages.gz](http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/binary-powerpc/Packages.gz)  404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/multiverse/binary-powerpc/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy/multiverse/binary-powerpc/Packages.gz)  404 Not Found [IP: 91.189.92.22 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/binary-powerpc/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/binary-powerpc/Packages.gz)  404 Not Found [IP: 91.189.92.22 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/main/binary-powerpc/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/main/binary-powerpc/Packages.gz)  404 Not Found [IP: 91.189.92.22 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/binary-powerpc/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/binary-powerpc/Packages.gz)  404 Not Found [IP: 91.189.92.22 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/binary-powerpc/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/binary-powerpc/Packages.gz)  404 Not Found [IP: 91.189.92.22 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/main/binary-powerpc/Packages.gz](http://security.ubuntu.com/ubuntu/dists/hardy-security/main/binary-powerpc/Packages.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/binary-powerpc/Packages.gz](http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/binary-powerpc/Packages.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/binary-powerpc/Packages.gz](http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/binary-powerpc/Packages.gz)  404 Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

It would seem that the PPC repositories are off-line.  If that's the case, the rest of you guys should have the same problem, right?

Any help getting my system configured correctly or affirming that we all have the problem would be much appreciated!

-DW

---

### Post by DaV|d on 2008-04-27
The first four links point to source repositories, which don't seem to be available on the ports archive. You can just untick "Source Code" and any entries referring to source code from "Third-Party Software" in the Software Sources tool. I don't know where the official binary repositories for ppc are located though.. Anyone with working repos?

---

### Post by stream303 on 2008-04-27
I had to follow these instructions from the xubuntu news page about ppc (applies to all ppc now)  and edit my /etc/apt/sources.list file:

[http://www.xubuntu.com/news/hardy/ports](http://www.xubuntu.com/news/hardy/ports)

All my repos are now "third party", and in the main Ubuntu tab, all the repos are UNchecked.  No updates have come in since the release is so new, but adding programs hasn't been a problem...

Update: I didn't read the release notes, but happily found that they are the same as the xubuntu notes, although they lack the trailing backslash:

[http://www.ubuntu.com/getubuntu/releasenotes/804](http://www.ubuntu.com/getubuntu/releasenotes/804)

So far, I have just simplified my sources.list file by uncommenting just three lines: (or just selecting these only in software sources)

```
deb http://ports.ubuntu.com/ubuntu-ports hardy main restricted

deb http://ports.ubuntu.com/ubuntu-ports hardy-updates main restricted

deb http://ports.ubuntu.com/ubuntu-ports hardy-security main restricted
```

and then did sudo apt-get update from the terminal..

---


---
title: "Trying to install g++ with UbuntuGuide need help"
date: 2006-02-07
forum: Absolute Beginner Talk
---

### Post by sirmoreno on 2006-02-07
i just installed unbuntu
i try to install repositories with sudo apt-get update and i get:

Err [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main Packages
  404 Not Found
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_main_binary-i386_Packages) - stat (2 No such file or directory)

and more...
and for the compiler : sudo apt-get install build-essential i get:

The following packages have unmet dependencies:
  build-essential: Depends: libc6-dev but it is not going to be installed or
                            libc-dev
                   Depends: g++ (>= 3:3.3) but it is not going to be installed
E: Broken packages

what to do??

---

### Post by kaamos on 2006-02-07
Are really running hoary (Ubuntu 5.04)? Or is just you sources.list incorrect? The newest release is Breezy (Ubuntu 5.10) and installing that is a good idea if you have not already.

---

### Post by sirmoreno on 2006-02-07
i have ubuntu 5.10
how can i know if the sources.list incorrect?

---

### Post by kaamos on 2006-02-07
Ubuntuguide.org is for 5.04.
Most of the stuff still works, but the sources mentioned there are only for hoary.

You can generate a new sources.list here -> [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)
Enabling at least universe, multiverse and backports is a good idea. Once you have replaced the old sources.list just do
```
sudo apt-get update && sudo apt-get install build-essential
```

---

### Post by sirmoreno on 2006-02-07
i still get

W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by kaamos on 2006-02-07
You need to replace _everything_ in your /etc/apt/sources.list with the file you get from [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic). Then do the command in the above post.

---

### Post by sirmoreno on 2006-02-07
Thank's a lot i think it worket
as you can tell i'm just begining, where can i find the g++ now?
are there any guides that can get me started?

---

### Post by kaamos on 2006-02-07
You can test that you have working g++ with the command
```
g++ --version
```

---

### Post by sirmoreno on 2006-02-07
this is only the compiler?
how can i get a working  environment like VC++? (debuger and everything)

---

### Post by kaamos on 2006-02-07
I'm not familiar with C programming, but I think anjuta could be what you are looking for. It can be installed with
```
sudo apt-get install anjuta
```

---

### Post by sirmoreno on 2006-02-07
thank's

---


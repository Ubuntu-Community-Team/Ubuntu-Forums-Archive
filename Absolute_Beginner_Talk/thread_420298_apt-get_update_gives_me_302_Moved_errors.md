---
title: "apt-get update gives me 302 Moved errors"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by mindstorm23 on 2007-04-23
I'm pretty new to Ubuntu and apt.  I'm trying to get the source of php5, so I tried running apt-get source php5, and I got the following error:

E: Could not open file /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_feisty_main_source_Sources - open (2 No such file or directory)

I assumed something was wrong with my source.list, so I regenerated my source.list from [http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/) which gave me this:

```
# Automatically generated sources.list
# http://www.ubuntu-nl.org/source-o-matic/
#
# If you get GPG errors with this sources.list, locate the GPG key in this file
# and run these commands (where KEY is replaced with that key)
#
# gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
# gpg --export --armor KEY | sudo apt-key add -
#
# If you don't know what to do with this file, read
# https://help.ubuntu.com/community/Repositories/CommandLine

# Ubuntu supported packages
# GPG key: 437D05B5
deb http://us.archive.ubuntu.com/ubuntu feisty main restricted 
deb http://us.archive.ubuntu.com/ubuntu feisty-updates main restricted
deb http://security.ubuntu.com/ubuntu feisty-security main restricted

deb-src http://us.archive.ubuntu.com/ubuntu feisty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu feisty-updates main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted

# Ubuntu community supported packages
# GPG key: 437D05B5
deb http://us.archive.ubuntu.com/ubuntu feisty universe multiverse 
deb http://us.archive.ubuntu.com/ubuntu feisty-updates universe multiverse
deb http://security.ubuntu.com/ubuntu feisty-security universe multiverse

deb-src http://us.archive.ubuntu.com/ubuntu feisty universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu feisty-updates universe multiverse
deb-src http://security.ubuntu.com/ubuntu feisty-security universe multiverse


```

After updating my sources.list with the new content, I ran apt-get update, and got the following:

```
Ign http://security.ubuntu.com feisty-security Release.gpg
Ign http://us.archive.ubuntu.com feisty Release.gpg
Ign http://security.ubuntu.com feisty-security/main Translation-en_US
Ign http://us.archive.ubuntu.com feisty/main Translation-en_US
Ign http://security.ubuntu.com feisty-security/restricted Translation-en_US
Ign http://us.archive.ubuntu.com feisty/restricted Translation-en_US
Ign http://security.ubuntu.com feisty-security/universe Translation-en_US
Ign http://us.archive.ubuntu.com feisty/universe Translation-en_US
Ign http://security.ubuntu.com feisty-security/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com feisty/multiverse Translation-en_US
Ign http://security.ubuntu.com feisty-security Release
Ign http://security.ubuntu.com feisty-security/main Packages
Ign http://us.archive.ubuntu.com feisty-updates Release.gpg
Ign http://security.ubuntu.com feisty-security/restricted Packages
Ign http://us.archive.ubuntu.com feisty-updates/main Translation-en_US
Ign http://security.ubuntu.com feisty-security/main Sources
Ign http://security.ubuntu.com feisty-security/restricted Sources
Ign http://us.archive.ubuntu.com feisty-updates/restricted Translation-en_US
Ign http://security.ubuntu.com feisty-security/universe Packages
Ign http://us.archive.ubuntu.com feisty-updates/universe Translation-en_US
Ign http://security.ubuntu.com feisty-security/multiverse Packages
Ign http://us.archive.ubuntu.com feisty-updates/multiverse Translation-en_US
Ign http://security.ubuntu.com feisty-security/universe Sources
Ign http://us.archive.ubuntu.com feisty Release
Ign http://security.ubuntu.com feisty-security/multiverse Sources
Err http://security.ubuntu.com feisty-security/main Packages
  302 Moved
Ign http://us.archive.ubuntu.com feisty-updates Release
Err http://security.ubuntu.com feisty-security/restricted Packages
  302 Moved
Err http://security.ubuntu.com feisty-security/main Sources
  302 Moved
Ign http://us.archive.ubuntu.com feisty/main Packages
Err http://security.ubuntu.com feisty-security/restricted Sources
  302 Moved
Ign http://us.archive.ubuntu.com feisty/restricted Packages
Err http://security.ubuntu.com feisty-security/universe Packages
  302 Moved
Err http://security.ubuntu.com feisty-security/multiverse Packages
  302 Moved
Ign http://us.archive.ubuntu.com feisty/main Sources
Err http://security.ubuntu.com feisty-security/universe Sources
  302 Moved
Ign http://us.archive.ubuntu.com feisty/restricted Sources
Err http://security.ubuntu.com feisty-security/multiverse Sources
  302 Moved
Ign http://us.archive.ubuntu.com feisty/universe Packages
Ign http://us.archive.ubuntu.com feisty/multiverse Packages
Ign http://us.archive.ubuntu.com feisty/universe Sources
Ign http://us.archive.ubuntu.com feisty/multiverse Sources
Ign http://us.archive.ubuntu.com feisty-updates/main Packages
Ign http://us.archive.ubuntu.com feisty-updates/restricted Packages
Ign http://us.archive.ubuntu.com feisty-updates/main Sources
Ign http://us.archive.ubuntu.com feisty-updates/restricted Sources
Ign http://us.archive.ubuntu.com feisty-updates/universe Packages
Ign http://us.archive.ubuntu.com feisty-updates/multiverse Packages
Ign http://us.archive.ubuntu.com feisty-updates/universe Sources
Ign http://us.archive.ubuntu.com feisty-updates/multiverse Sources
Err http://us.archive.ubuntu.com feisty/main Packages
  302 Moved [IP: 130.239.18.158 80]
Err http://us.archive.ubuntu.com feisty/restricted Packages
  302 Moved [IP: 130.239.18.158 80]
Err http://us.archive.ubuntu.com feisty/main Sources
  302 Moved [IP: 130.239.18.158 80]
Err http://us.archive.ubuntu.com feisty/restricted Sources
  302 Moved [IP: 130.239.18.158 80]
Err http://us.archive.ubuntu.com feisty/universe Packages
  302 Moved [IP: 130.239.18.158 80]
Err http://us.archive.ubuntu.com feisty/multiverse Packages
  302 Moved [IP: 130.239.18.158 80]
Err http://us.archive.ubuntu.com feisty/universe Sources
  302 Moved [IP: 130.239.18.158 80]
Err http://us.archive.ubuntu.com feisty/multiverse Sources
  302 Moved [IP: 130.239.18.158 80]
Err http://us.archive.ubuntu.com feisty-updates/main Packages
  302 Moved [IP: 130.239.18.158 80]
Err http://us.archive.ubuntu.com feisty-updates/restricted Packages
  302 Moved [IP: 130.239.18.158 80]
Err http://us.archive.ubuntu.com feisty-updates/main Sources
  302 Moved [IP: 130.239.18.158 80]
Err http://us.archive.ubuntu.com feisty-updates/restricted Sources
  302 Moved [IP: 130.239.18.158 80]
Err http://us.archive.ubuntu.com feisty-updates/universe Packages
  302 Moved [IP: 130.239.18.158 80]
Err http://us.archive.ubuntu.com feisty-updates/multiverse Packages
  302 Moved [IP: 130.239.18.158 80]
Err http://us.archive.ubuntu.com feisty-updates/universe Sources
  302 Moved [IP: 130.239.18.158 80]
Err http://us.archive.ubuntu.com feisty-updates/multiverse Sources
  302 Moved [IP: 130.239.18.158 80]
Reading package lists...
Failed to fetch http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.gz  302 Moved
Failed to fetch http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/binary-i386/Packages.gz  302 Moved
Failed to fetch http://security.ubuntu.com/ubuntu/dists/feisty-security/main/source/Sources.gz  302 Moved
Failed to fetch http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/source/Sources.gz  302 Moved
Failed to fetch http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/binary-i386/Packages.gz  302 Moved
Failed to fetch http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/binary-i386/Packages.gz  302 Moved
Failed to fetch http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/source/Sources.gz  302 Moved
Failed to fetch http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/source/Sources.gz  302 Moved
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz  302 Moved [IP: 130.239.18.158 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz  302 Moved [IP: 130.239.18.158 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz  302 Moved [IP: 130.239.18.158 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/feisty/restricted/source/Sources.gz  302 Moved [IP: 130.239.18.158 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz  302 Moved [IP: 130.239.18.158 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz  302 Moved [IP: 130.239.18.158 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.gz  302 Moved [IP: 130.239.18.158 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/source/Sources.gz  302 Moved [IP: 130.239.18.158 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/binary-i386/Packages.gz  302 Moved [IP: 130.239.18.158 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/binary-i386/Packages.gz  302 Moved [IP: 130.239.18.158 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/source/Sources.gz  302 Moved [IP: 130.239.18.158 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/source/Sources.gz  302 Moved [IP: 130.239.18.158 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/universe/binary-i386/Packages.gz  302 Moved [IP: 130.239.18.158 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/multiverse/binary-i386/Packages.gz  302 Moved [IP: 130.239.18.158 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/universe/source/Sources.gz  302 Moved [IP: 130.239.18.158 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/multiverse/source/Sources.gz  302 Moved [IP: 130.239.18.158 80]
E: Some index files failed to download, they have been ignored, or old ones used instead.
```

I'm not really sure what to do.  Needless to say, apt-get source php5 still gives me the same error.  Ideas?

---

### Post by mindstorm23 on 2007-04-23
I forgot to mention - I think I'm behind a proxy.  Might that be related to the problem?

When I installed, it asked me if the server was behind a proxy.  I said no, and apt has been working fine, but now php5 will not work.

---

### Post by mindstorm23 on 2007-04-23
I hate to keep replying to my own post, but I found out some more:

I found where the 302 originates from.  I tried doing "wget www.google.com" and the request, when going through my proxy, threw back a HTTP 302 Moved.  It then tried to move me to a different URL on my proxy:

[http://172.16.28.9:15871/cgi-bin/authenticate.cgi?ws-session=687871189](http://172.16.28.9:15871/cgi-bin/authenticate.cgi?ws-session=687871189)

and couldn't authenticate, giving me a HTTP 401 unauthorized.

So now my question is: how do I configure Ubuntu to figure out my proxy??

---

### Post by mindstorm23 on 2007-04-25
Alright, I think I found out why I was getting all these issues: the network I'm on filters everything through Websense, a filtering program.  It's not a proxy.  It uses Windows logons and Active Directory to determine who is accessing the internet and keeps a log of every request.  Since my box was offering no Windows authentication, it rejected me.

So, not my question is: how do I set up my box to offer a windows login to Websense every time it accesses th internet?  I know wget has some built-in, but apt-get does not, and that's the one I need...

---

### Post by somabc on 2007-11-16
> **mindstorm23 said:**
> Alright, I think I found out why I was getting all these issues: the network I'm on filters everything through Websense, a filtering program.  It's not a proxy.  It uses Windows logons and Active Directory to determine who is accessing the internet and keeps a log of every request.  Since my box was offering no Windows authentication, it rejected me.

So, not my question is: how do I set up my box to offer a windows login to Websense every time it accesses th internet?  I know wget has some built-in, but apt-get does not, and that's the one I need...

I have this exact same problem if anyone has found a solution please let me know!

---


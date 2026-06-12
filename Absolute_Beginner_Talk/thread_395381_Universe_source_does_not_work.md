---
title: "Universe source does not work"
date: 2007-03-28
forum: Absolute Beginner Talk
---

### Post by rockymaxsource on 2007-03-28
Hey,

I got the following content in my sources.list file > # Automatically generated sources.list
# [http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)
#
# If you get GPG errors with this sources.list, locate the GPG key in this file
# and run these commands (where KEY is replaced with that key)
#
# gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
# gpg --export --armor KEY | sudo apt-key add -
#
# If you don't know what to do with this file, read
# [https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)

# Ubuntu supported packages
# GPG key: 437D05B5
deb [http://cn.archive.ubuntu.com/ubuntu](http://cn.archive.ubuntu.com/ubuntu) edgy main restricted 
deb [http://cn.archive.ubuntu.com/ubuntu](http://cn.archive.ubuntu.com/ubuntu) edgy-updates main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted

# Ubuntu community supported packages
# GPG key: 437D05B5
deb [http://cn.archive.ubuntu.com/ubuntu](http://cn.archive.ubuntu.com/ubuntu) edgy universe multiverse 
deb [http://cn.archive.ubuntu.com/ubuntu](http://cn.archive.ubuntu.com/ubuntu) edgy-updates universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe multiverse

# Ubuntu backports project
# GPG key: 437D05B5
deb [http://cn.archive.ubuntu.com/ubuntu](http://cn.archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse 

#Skype
deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free



When I try to install  cabextract. I got the error of no package is available.
sudo apt-get update gives me the following error.
> 99% [5 Packages gzip 0] [Waiting for headers] [Connecting to download.skype.com
gzip: stdin: not in gzip format
Err [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) edgy/universe Packages                        
  Sub-process gzip returned an error code (1)


Can any of you help me out please?

Thanks a lot in advance!
Rocky

---

### Post by seshomaru samma on 2007-03-28
Is CN China?
I  live in China and I use these repos (very fast):
```
deb http://ubuntu.cn99.com/ubuntu/ dapper main restricted universe multiverse
deb http://ubuntu.cn99.com/ubuntu/ dapper-updates main restricted universe multiverse
deb http://ubuntu.cn99.com/ubuntu/ dapper-security main restricted universe multiverse
deb http://ubuntu.cn99.com/ubuntu/ dapper-backports main restricted universe multiverse
deb http://ubuntu.cn99.com/ubuntu-cn/ dapper main restricted universe multiverse
```

---


---
title: "adept_installer problem"
date: 2008-01-02
forum: Absolute Beginner Talk
---

### Post by youit on 2008-01-02
I am totally new to Linux 
Have just installed Kubuntu and did try to get it to play mp3 

I went and checked universe tab but couldn't find any players / codecs in the add new programs adept_installer app . 

I   added "http://packages.ubuntu.com/gutsy/libs/libxine1-ffmpeghttp://packages.ubuntu.com/gutsy/libs/libxine1-ffmpeg"
without the "deb" in the beginning.
This is the last line of the '/etc/apt/sources.list ' file 

Now when I try to run the adept_installer I get this ERROR :
"The APT Database could not be opened! This may be caused by incorrect APT configuration or some similar problem. Try running apt-setup and apt-get update in terminal and see if it helps to resolve the problem."

The setup and getupdate give me errors . 
The apt-getupdate gives : "E: Type 'http://packages.ubuntu.com/gutsy/libs/libxine1-ffmpeghttp://packages.ubuntu.com/gutsy/libs/libxine1-ffmpeg' is not known on line 75 in source list /etc/apt/sources.list"

The apt-setup gives : "/bin/sh: apt-setup: not found"

Help me here ppl .
How can I delete this line ??

---

### Post by wolfen69 on 2008-01-02
go here: [http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/) and replace your sources.list. then sudo apt-get upate, then just go to add/remove programs, go to pull down menu at the top, and select all available applications. then search for  kubuntu restricted extras.install and done.

---

### Post by wolfen69 on 2008-01-02
hereis what your sources.list should look like:
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
deb http://us.archive.ubuntu.com/ubuntu gutsy main restricted 
deb http://us.archive.ubuntu.com/ubuntu gutsy-updates main restricted
deb http://security.ubuntu.com/ubuntu gutsy-security main restricted

# Ubuntu community supported packages
# GPG key: 437D05B5
deb http://us.archive.ubuntu.com/ubuntu gutsy universe multiverse 
deb http://us.archive.ubuntu.com/ubuntu gutsy-updates universe multiverse
deb http://security.ubuntu.com/ubuntu gutsy-security universe multiverse

# Ubuntu backports project
# GPG key: 437D05B5
deb http://us.archive.ubuntu.com/ubuntu gutsy-backports main restricted universe multiverse 

# Upstream Opera
# GPG key: 6A423791
deb http://deb.opera.com/opera etch non-free 

```

---

### Post by youit on 2008-01-03
Thanks a lot for that quick help. 


adept's working fine now .
and even my mp3s are running in amarok .

---

### Post by PeterJS on 2008-01-03
Word of advice, Adept is probably the worst of the apt frontends, I started off with KDE back in the day and even using KDE one of the first things I install is Synaptic. It's just got more features, more polish, and things are easier to find.

---


---
title: "where is VLC 0.8.6d ???  only i can find 0.8.6C in ubuntu"
date: 2007-12-26
forum: Absolute Beginner Talk
---

### Post by DO55 on 2007-12-26
hi 
 
im trying to have the latest update of VLC which  is 0.8.6d  but when i try to download it from ubuntu   only i found the old one 0.8.6C 
the new one have many fixs 
look
[http://trac.videolan.org/vlc/browser/tags/0.8.6d/NEWS](http://trac.videolan.org/vlc/browser/tags/0.8.6d/NEWS)

---

### Post by LowSky on 2007-12-26
you could always add debian (sid) repositories and install the newest that way.
Or wait until ubuntu is done testing it and it is released by them.

here are the debian repos, open synaptic got to settings>repositories
```

deb http://download.videolan.org/pub/videolan/debian sid main
deb-src http://download.videolan.org/pub/videolan/debian sid main

```

after adding them to synaptic open terminal and type
```
apt-get update
```
```
apt-get install vlc libdvdcss2
```

---

### Post by AndyCooll on 2007-12-26
> **DO55 said:**
> hi 
 
im trying to have the latest update of VLC which  is 0.8.6d  but when i try to download it from ubuntu   only i found the old one 0.8.6C 
the new one have many fixs 
look
[http://trac.videolan.org/vlc/browser/tags/0.8.6d/NEWS](http://trac.videolan.org/vlc/browser/tags/0.8.6d/NEWS)

That's likely to be because when the Gutsy release was frozen only 0.8.6c was officially available. 

Newer releases of apps then do not get added to the repos unless there are security issues or it's a significant enough release to be considered for backports. I read somewhere that although 0.8.6d was for a security update, it was a vulnerability that only affected Windows/Mac users anyway.

So it probably won't turn up until Hardy.

:cool:

---

### Post by Hospadar on 2007-12-26
a lot of software in the repos isn't the newest version because it takes package maintainers a little while to build and test packages for each new version.  So if you can't *the* newest version, you'll generally need to get it from the original developer.  that said, generally it can be helpful to install the older package to pick up all the needed dependencies, and then remove it before installing the newest version (If the developer lets you download a .deb you don't need to worry about this, only worry if they provide non-native packages like .rpm or just shell scripts for the install). Although, if you're building from source you'll need the "*-dev" header packages for whatever libraries it builds with.

---


---
title: "ubuntu gutsy hangs after login"
date: 2008-02-26
forum: Absolute Beginner Talk
---

### Post by rakhi on 2008-02-26
Hi,

I'm a complete n00bie and was very proud of myself for having installed dual boot linux/windows on my new IBM laptop...sadly when I tried to boot into linux again this morning things only seem to work until after I login, when ubuntu hangs on a blank brown screen :(

I tried to follow the instructions on 

[http://ubuntuforums.org/showthread.php?t=324849](http://ubuntuforums.org/showthread.php?t=324849)

which involve updating apt-get but I get a string of error messages like 

> Could not resolve 'us.archive.ubuntu.com'

This makes me think it's some network issue.  

One piece of possibly related info is that when I first booted back into windows yesterday (after working in linux) for some reason the windows network manager was disabled, and I had to renable it manually.

---

### Post by sayakb on 2008-02-26
> **rakhi said:**
> Hi,

I'm a complete n00bie and was very proud of myself for having installed dual boot linux/windows on my new IBM laptop...sadly when I tried to boot into linux again this morning things only seem to work until after I login, when ubuntu hangs on a blank brown screen :(

I tried to follow the instructions on 

[http://ubuntuforums.org/showthread.php?t=324849](http://ubuntuforums.org/showthread.php?t=324849)

which involve updating apt-get but I get a string of error messages like 



This makes me think it's some network issue.  

One piece of possibly related info is that when I first booted back into windows yesterday (after working in linux) for some reason the windows network manager was disabled, and I had to renable it manually.

Unplug your network cable and try booting in.

---

### Post by rakhi on 2008-02-26
did that already, still the same problem.  Maybe it's the wireless?

---

### Post by sayakb on 2008-02-26
> **rakhi said:**
> did that already, still the same problem.  Maybe it's the wireless?

Generally during installation, gutsy tries to download security updates. If it fails, it adds it to the sources.lst file. If you have the wireless off and network unplugged, you should not face this problem. Wait for others' responses..

---


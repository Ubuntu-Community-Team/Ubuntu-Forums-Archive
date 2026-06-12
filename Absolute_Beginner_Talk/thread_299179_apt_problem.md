---
title: "apt problem"
date: 2006-11-13
forum: Absolute Beginner Talk
---

### Post by fish456 on 2006-11-13
First things first, with regards to the sticky "thinking about upgrading to edgy" (you can find it in the stickies above this post). Are the edgy servers still overloaded, because that could be the source of my problem.

Now, on to the problem, this just drives me nuts. On updating my repositories (or installing things, or ... you know), I get more of these errors than actual succesfull updates.
```
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-updates/multiverse/binary-i386/Packages.gz  Error reading from server - read (104 Connection reset by peer) [IP: 195.248.90.35 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-updates/main/source/Sources.gz  Error reading from server - read (104 Connection reset by peer) [IP: 195.248.90.35 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/source/Sources.gz  Error reading from server - read (104 Connection reset by peer) [IP: 195.248.90.35 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/source/Sources.gz  Error reading from server - read (104 Connection reset by peer) [IP: 195.248.90.35 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-backports/main/binary-i386/Packages.gz  Error reading from server - read (104 Connection reset by peer) [IP: 195.248.90.35 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-backports/restricted/binary-i386/Packages.gz  Error reading from server - read (104 Connection reset by peer) [IP: 195.248.90.35 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-backports/universe/binary-i386/Packages.gz  Error reading from server - read (104 Connection reset by peer) [IP: 195.248.90.35 80]

```

There is obviously something wrong between my computer and the ubuntu servers. I tried to change the prefixes on the links ([http://archive](http://archive).... to [http://en.archive](http://en.archive)...) and so forth, but the problem persists.
I should also mention that I am on my university network (kotnet, for the people who want to know). It is a metropolean area network (almost the whole city has internet via kotnet, especially the students). Maybe it has a proxy server, but I doubt that is the problem, because the uni is kind of big on ubuntu. I think they would come to that problem and solve it themselves. 
Does anybody have any ideas?
It is really killing me because I had to reinstall and now I am stuck without firefox, java, codecs, ...

---

### Post by SephirothXIIIX on 2006-11-13
Connection reset by peer? That sounds like a timeout..

I just recently used the Edgy servers, they appear to be fine. Maybe you should try a hard connection if you're running on Wifi, or a more stable one if you aren't.

---

### Post by fish456 on 2006-11-13
gah, stupid of me, I wouldn't have thought of that. I was on wifi, I forgot ](*,) 
I just ran apt-get update, and there are indeed less errors. 
This time, you get the full output:
```
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy/Release.gpg  Error reading from server - read (104 Connection reset by peer) [IP: 195.248.90.38 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-updates/Release.gpg  Error reading from server - read (104 Connection reset by peer) [IP: 195.248.90.38 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-backports/Release.gpg  Error reading from server - read (104 Connection reset by peer) [IP: 195.248.90.38 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-proposed/universe/binary-i386/Packages.bz2  Sub-process bzip2 returned an error code (2)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-proposed/multiverse/binary-i386/Packages.bz2  Sub-process bzip2 returned an error code (2)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-updates/main/binary-i386/Packages.bz2  Sub-process bzip2 returned an error code (2)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/binary-i386/Packages.bz2  Sub-process bzip2 returned an error code (2)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-updates/multiverse/binary-i386/Packages.bz2  Sub-process bzip2 returned an error code (2)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-updates/main/source/Sources.bz2  Sub-process bzip2 returned an error code (2)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/source/Sources.bz2  Sub-process bzip2 returned an error code (2)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-updates/multiverse/source/Sources.bz2  Sub-process bzip2 returned an error code (2)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-backports/main/binary-i386/Packages.bz2  Sub-process bzip2 returned an error code (2)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-backports/restricted/binary-i386/Packages.bz2  Sub-process bzip2 returned an error code (2)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-backports/universe/binary-i386/Packages.bz2  Sub-process bzip2 returned an error code (2)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy/main/binary-i386/Packages.gz  Error reading from server - read (104 Connection reset by peer) [IP: 195.248.90.38 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy/restricted/binary-i386/Packages.gz  Sub-process gzip returned an error code (1)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz  Error reading from server - read (104 Connection reset by peer) [IP: 195.248.90.38 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy/multiverse/binary-i386/Packages.gz  Error reading from server - read (104 Connection reset by peer) [IP: 195.248.90.38 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy/main/source/Sources.gz  Error reading from server - read (104 Connection reset by peer) [IP: 195.248.90.38 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy/universe/source/Sources.gz  Error reading from server - read (104 Connection reset by peer) [IP: 195.248.90.38 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy/multiverse/source/Sources.gz  Error reading from server - read (104 Connection reset by peer) [IP: 195.248.90.38 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-proposed/main/binary-i386/Packages.gz  Sub-process gzip returned an error code (1)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-proposed/restricted/binary-i386/Packages.gz  Error reading from server - read (104 Connection reset by peer) [IP: 195.248.90.38 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/binary-i386/Packages.gz  Error reading from server - read (104 Connection reset by peer) [IP: 195.248.90.38 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/source/Sources.gz  Error reading from server - read (104 Connection reset by peer) [IP: 195.248.90.38 80]

```

---

### Post by fish456 on 2006-11-14
bump

---

### Post by Bachstelze on 2006-11-14
Definitely a network problem of yours, nothing to do with apt.

---

### Post by DannyG on 2006-11-14
Are you sure your Wifi is working properly? Can you access any web pages? Also, make sure your Router is accepting your Wifi connection and not blocking it from the Network...

---


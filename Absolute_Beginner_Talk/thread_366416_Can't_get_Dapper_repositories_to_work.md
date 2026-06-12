---
title: "Can't get Dapper repositories to work"
date: 2007-02-20
forum: Absolute Beginner Talk
---

### Post by gr0kzer0 on 2007-02-20
I kinda recently installed Dapper, and just got my internet connection going.  In Synaptic I tried to enable all the repositories.  Then I hit the reload, to update it all, and ended up with this error message: None of these are working, or need updating or some such:
> [http://gb.archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz:](http://gb.archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz:) 502 Bad Gateway
[http://gb.archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz:](http://gb.archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz:) 502 Bad Gateway
[http://gb.archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz:](http://gb.archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz:) 502 Bad Gateway
[http://gb.archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources.gz:](http://gb.archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources.gz:) 502 Bad Gateway
[http://gb.archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz:](http://gb.archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz:) 502 Bad Gateway
[http://gb.archive.ubuntu.com/ubuntu/dists/dapper/universe/source/Sources.gz:](http://gb.archive.ubuntu.com/ubuntu/dists/dapper/universe/source/Sources.gz:) 502 Bad Gateway
[http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.gz:) 502 Bad Gateway
[http://gb.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz:](http://gb.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz:) 502 Bad Gateway
[http://gb.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz:](http://gb.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz:) 502 Bad Gateway
[http://gb.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz:](http://gb.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz:) 502 Bad Gateway
[http://gb.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/source/Sources.gz:](http://gb.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/source/Sources.gz:) 502 Bad Gateway
[http://gb.archive.ubuntu.com/ubuntu/dists/dapper-backports/main/binary-i386/Packages.gz:](http://gb.archive.ubuntu.com/ubuntu/dists/dapper-backports/main/binary-i386/Packages.gz:) 502 Bad Gateway
[http://gb.archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/binary-i386/Packages.gz:](http://gb.archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/binary-i386/Packages.gz:) 502 Bad Gateway
[http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/binary-i386/Packages.gz:) 502 Bad Gateway
[http://security.ubuntu.com/ubuntu/dists/dapper-security/main/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/dapper-security/main/source/Sources.gz:) 502 Bad Gateway
[http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/source/Sources.gz:) 502 Bad Gateway
[http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.gz:) 502 Bad Gateway
[http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/source/Sources.gz:) 502 Bad Gateway
[http://gb.archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/binary-i386/Packages.gz:](http://gb.archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/binary-i386/Packages.gz:) 502 Bad Gateway
[http://gb.archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/binary-i386/Packages.gz:](http://gb.archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/binary-i386/Packages.gz:) 502 Bad Gateway
[http://gb.archive.ubuntu.com/ubuntu/dists/dapper-backports/main/source/Sources.gz:](http://gb.archive.ubuntu.com/ubuntu/dists/dapper-backports/main/source/Sources.gz:) 502 Bad Gateway
[http://gb.archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/source/Sources.gz:](http://gb.archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/source/Sources.gz:) 502 Bad Gateway
[http://gb.archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/source/Sources.gz:](http://gb.archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/source/Sources.gz:) 502 Bad Gateway
[http://gb.archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/source/Sources.gz:](http://gb.archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/source/Sources.gz:) 502 Bad Gateway


I want to get Dapper working decently, I wanna be able to play mp3s in Rythmbox, DVDs in Totem or whatever movie player is best, plus all the other kinds of stuff regular folk get to do.  But I can't!! Pleeeze, what do I do so I can run Dapper like "normal" "people"?

Cheerz.

---

### Post by Bachstelze on 2007-02-20
Can you ping external websites ? In a terminal, do

```
ping -c 4 www.google.com
```

---

### Post by gr0kzer0 on 2007-02-20
> Can you ping external websites ? In a terminal, do

Code:

ping -c 4 [www.google.com](www.google.com)
t0p@t0p-desktop:~$ ping -c 4 [www.google.com](www.google.com)
PING [www.l.google.com](www.l.google.com) (216.239.37.99) 56(84) bytes of data.
64 bytes from va-in-f99.google.com (216.239.37.99): icmp_seq=1 ttl=230 time=722 ms
64 bytes from va-in-f99.google.com (216.239.37.99): icmp_seq=2 ttl=232 time=854 ms
64 bytes from va-in-f99.google.com (216.239.37.99): icmp_seq=3 ttl=230 time=891 ms
64 bytes from va-in-f99.google.com (216.239.37.99): icmp_seq=4 ttl=230 time=871 ms

--- [www.l.google.com](www.l.google.com) ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 4709ms
rtt min/avg/max/mdev = 722.257/835.056/891.726/66.446 ms
t0p@t0p-desktop:~$



Yes, I can.

t0p@t0p-desktop:~$ ping -c 4 [www.google.com](www.google.com)
PING [www.l.google.com](www.l.google.com) (216.239.37.99) 56(84) bytes of data.
64 bytes from va-in-f99.google.com (216.239.37.99): icmp_seq=1 ttl=230 time=722 ms
64 bytes from va-in-f99.google.com (216.239.37.99): icmp_seq=2 ttl=232 time=854 ms
64 bytes from va-in-f99.google.com (216.239.37.99): icmp_seq=3 ttl=230 time=891 ms
64 bytes from va-in-f99.google.com (216.239.37.99): icmp_seq=4 ttl=230 time=871 ms

--- [www.l.google.com](www.l.google.com) ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 4709ms
rtt min/avg/max/mdev = 722.257/835.056/891.726/66.446 ms
t0p@t0p-desktop:~$

Is there a way to fix the list of repositories I've got, so I can use ones that other folk use successfully?  Or is there something wrong with my set-up?  I'm currently restricted to playing .ogg format music files in Rhythmbox cos I don't know how to get hold of and use the .mp3 codec, and I have to use the DVD player in my Win2000 partition to watch movies.  And I DON'T WANNA LIVE LIKE THIS!!

---

### Post by Bachstelze on 2007-02-20
Try running this, does the connection to the repos work ?

```
sudo apt-get update
```

---


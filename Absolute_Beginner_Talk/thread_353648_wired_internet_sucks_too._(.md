---
title: "wired internet sucks too. :("
date: 2007-02-04
forum: Absolute Beginner Talk
---

### Post by lunaz on 2007-02-04
so after getting no where making belkin usb work i re installed ubuntu on the old comp & drug my router/modem combo out (actiontec wireless...) i plugged it in, unplugged the usb wireless thing, and even turned off wireless in the router. internet starts out ok then goes slower then stops. what gives? did i pick the wrong distro or am i missing something? ubuntu's network settings is set for dhcp, router is set for pppoa, isp name/pass, dynamic ip/dns config

just don't see how i can learn to do this w/o the internet working right (wired or not)...and i sure want to learn it.

---

### Post by phossal on 2007-02-05
Any chance you're noticing sluggishness from the net while it's *downloading updates*. One of the first things you should do on a new system is enable all the repositories and then run:
```
sudo apt-get update
sudo apt-get upgrade
```
Sometimes I'll realize that my system is suddenly slowing down, and my net isn't rockin', and then next thing I know, the little "system update" icon appears. 

Check it out and then report back.

---

### Post by Spr0k3t on 2007-02-05
One thing you may want to check is your DNS settings on the router.  I would recommend checking out OpenDNS.org and setting up an account.  Second thing to check is to see if you have IPV6 turned on or not.  If you have this on I would recommend disabling it as a test.

On my desktop PC, I couldn't connect to any networks until I disabled IPV6 and disabled the card in System/Administrator/Networking...  Not sure why though, but it works that way.

[How-To: Disable IPV6 to speed up Internet.](http://www.ubuntuforums.org/showthread.php?t=87798)

---

### Post by lunaz on 2007-02-07
wow, ty :D disabling ipv6 in flrefox seem to help. i have another question tho. i went to system>admin>software preferences, then enabled all the repositories that were unchecked (universe/multiverse source/bin), and reloaded it. now it's stuck at failing most of the updates. is this an internet thing & i need to do more setup or is it a something dumb i did thing? haha.

---

### Post by r4ik on 2007-02-07
Type about:config in the adressbar and set the "pipe" maxrequest to 8

---

### Post by lunaz on 2007-02-07
well, today i tried to update teh comp again while i was at work, got home & most of em failed. i went to about:config In firefox & changed the pipe maxrequest to 8, tried the update thing again, failed. so then i tried sudo apt-get update, and here's the output. sorry its so long.

```

gail@gail-oldpos:~$ sudo apt-get update
Password:
Err http://ca.archive.ubuntu.com dapper Release.gpg
  Could not connect to ca.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Networ k is unreachable)
Err http://ca.archive.ubuntu.com dapper-updates Release.gpg
  Could not connect to ca.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Networ k is unreachable)
Err http://ca.archive.ubuntu.com dapper-backports Release.gpg
  Could not connect to ca.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Networ k is unreachable)
Ign http://ca.archive.ubuntu.com dapper Release
Ign http://ca.archive.ubuntu.com dapper-updates Release
Err http://security.ubuntu.com dapper-security Release.gpg
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err http://ca.archive.ubuntu.com dapper-backports Release

Ign http://ca.archive.ubuntu.com dapper/main Packages
Ign http://ca.archive.ubuntu.com dapper/restricted Packages
Ign http://ca.archive.ubuntu.com dapper/main Sources
Ign http://ca.archive.ubuntu.com dapper/restricted Sources
Ign http://ca.archive.ubuntu.com dapper/universe Packages
Ign http://ca.archive.ubuntu.com dapper/universe Sources
Ign http://ca.archive.ubuntu.com dapper-updates/main Packages
Ign http://ca.archive.ubuntu.com dapper-updates/restricted Packages
Ign http://ca.archive.ubuntu.com dapper-updates/main Sources
Ign http://ca.archive.ubuntu.com dapper-updates/restricted Sources
Ign http://ca.archive.ubuntu.com dapper-backports/main Packages
Ign http://ca.archive.ubuntu.com dapper-backports/restricted Packages
Ign http://ca.archive.ubuntu.com dapper-backports/universe Packages
Ign http://ca.archive.ubuntu.com dapper-backports/multiverse Packages
Ign http://ca.archive.ubuntu.com dapper-backports/main Sources
Ign http://ca.archive.ubuntu.com dapper-backports/restricted Sources
Ign http://ca.archive.ubuntu.com dapper-backports/universe Sources
Ign http://ca.archive.ubuntu.com dapper-backports/multiverse Sources
Err http://ca.archive.ubuntu.com dapper/main Packages
  Could not connect to ca.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err http://ca.archive.ubuntu.com dapper/restricted Packages
  Could not connect to ca.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err http://ca.archive.ubuntu.com dapper/main Sources
  Could not connect to ca.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err http://ca.archive.ubuntu.com dapper/restricted Sources
  Could not connect to ca.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err http://ca.archive.ubuntu.com dapper/universe Packages
  Could not connect to ca.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err http://ca.archive.ubuntu.com dapper/universe Sources
  Could not connect to ca.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err http://ca.archive.ubuntu.com dapper-updates/main Packages
  Could not connect to ca.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err http://ca.archive.ubuntu.com dapper-updates/restricted Packages
  Could not connect to ca.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err http://ca.archive.ubuntu.com dapper-updates/main Sources
  Could not connect to ca.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err http://ca.archive.ubuntu.com dapper-updates/restricted Sources
  Could not connect to ca.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err http://ca.archive.ubuntu.com dapper-backports/main Packages
  Could not connect to ca.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err http://ca.archive.ubuntu.com dapper-backports/restricted Packages
  Could not connect to ca.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err http://ca.archive.ubuntu.com dapper-backports/universe Packages
  Could not connect to ca.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err http://ca.archive.ubuntu.com dapper-backports/multiverse Packages
  Could not connect to ca.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err http://ca.archive.ubuntu.com dapper-backports/main Sources
  Could not connect to ca.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err http://ca.archive.ubuntu.com dapper-backports/restricted Sources
  Could not connect to ca.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err http://ca.archive.ubuntu.com dapper-backports/universe Sources
  Could not connect to ca.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err http://ca.archive.ubuntu.com dapper-backports/multiverse Sources
  Could not connect to ca.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg Could not connect to ca.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg Could not connect to ca.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg Could not connect to ca.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/dapper-backports/Release
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz Could not connect to ca.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz Could not connect to ca.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz Could not connect to ca.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources.gz Could not connect to ca.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz Could not connect to ca.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/dapper/universe/source/Sources.gz Could not connect to ca.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz Could not connect to ca.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz Could not connect to ca.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz Could not connect to ca.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/source/Sources.gz Could not connect to ca.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/dapper-backports/main/binary-i386/Packages.gz Could not connect to ca.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/binary-i386/Packages.gz Could not connect to ca.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/binary-i386/Packages.gz Could not connect to ca.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/binary-i386/Packages.gz Could not connect to ca.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/dapper-backports/main/source/Sources.gz Could not connect to ca.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/source/Sources.gz Could not connect to ca.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/source/Sources.gz Could not connect to ca.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/source/Sources.gz Could not connect to ca.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used instead.
gail@gail-oldpos:~$
```

is there any other info needed? i appreciate all the help here, and yes, firefox works decent now. :D
forgot to mention, gaim doesn't connect either.

---


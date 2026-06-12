---
title: "unable to update or add programmes"
date: 2006-12-12
forum: Absolute Beginner Talk
---

### Post by vaio pcgfxa53 dapper on 2006-12-12
New to linux and a freind sugested Ubuntu.  I am running an older viao laptop model pcgfxa53 with Dapper.

I am unable to update dapper neither using the critical updates, the synaptic package manager, or apt.  Automatix also will not install.  I am up on line without any probs, no proxy or firewall restrictions and I am behind a neatgear wireless router with an ra2500 chipset card.


I have tried updating the repository but that did not work either.

output from sudo apt-get update is as follows:

boss@boss-laptop:~$ lynx --dump http://`hostname`/mywiki?action=test
bash: lynx: command not found
boss@boss-laptop:~$ sudo apt-get update
Password:
Err [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release.gpg
  Could not connect to archive.canonical.com:80 (1.0.0.0), connection timed out
Err [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) dapper-updates Release.gpg
  Could not connect to fr.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release.gpg
  Could not connect to packages.freecontrib.org:80 (1.0.0.0), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg)  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg)  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg)  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed outFailed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg)  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://archive.canonical.com/ubuntu/dists/dapper-commercial/Release.gpg](http://archive.canonical.com/ubuntu/dists/dapper-commercial/Release.gpg)  Could not connect to archive.canonical.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://packages.freecontrib.org/plf/dists/dapper/Release.gpg](http://packages.freecontrib.org/plf/dists/dapper/Release.gpg)  Could not connect to packages.freecontrib.org:80 (1.0.0.0), connection timed out
Failed to fetch [http://fr.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg](http://fr.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg)  Could not connect to fr.archive.ubuntu.com:80 (1.0.0.0), connection timed out

---

### Post by Kobalt on 2006-12-12
Simple question : do you have a working internet connection on Ubuntu ? Did you configure your wifi card ?

---

### Post by vaio pcgfxa53 dapper on 2006-12-12
yes to both, no broblem online, wifi is correctly setup, ipv6 is off in mozilla (my isp only supports ipv4)

---

### Post by vaio pcgfxa53 dapper on 2006-12-12
also ran sudo app-get updates output is as follows;

boss@boss-laptop:~$ sudo apt-get update
Password:
Err [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) dapper Release.gpg
  Could not connect to fr.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg
  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) dapper-updates Release.gpg
  Could not connect to fr.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Err [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) dapper Release

Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Err [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) dapper-updates Release

Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Ign [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) dapper/main Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Ign [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) dapper/restricted Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Ign [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) dapper/main Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Ign [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) dapper/restricted Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Ign [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) dapper-updates/main Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Ign [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) dapper-updates/restricted Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Ign [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) dapper-updates/main Sources
Ign [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) dapper-updates/restricted Sources
Err [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) dapper/main Packages
  Could not connect to fr.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) dapper/restricted Packages
  Could not connect to fr.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) dapper/main Sources
  Could not connect to fr.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) dapper/restricted Sources
  Could not connect to fr.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) dapper-updates/main Packages
  Could not connect to fr.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) dapper-updates/restricted Packages
  Could not connect to fr.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) dapper-updates/main Sources
  Could not connect to fr.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) dapper-updates/restricted Sources
  Could not connect to fr.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://fr.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg](http://fr.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg)  Could not connect to fr.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Failed to fetch [http://fr.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg](http://fr.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg)  Could not connect to fr.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg)  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Failed to fetch [http://fr.archive.ubuntu.com/ubuntu/dists/dapper/Release](http://fr.archive.ubuntu.com/ubuntu/dists/dapper/Release)
Failed to fetch [http://fr.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release](http://fr.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.gz)  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/binary-i386/Packages.gz)  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://fr.archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz](http://fr.archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz)  Could not connect to fr.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/main/source/Sources.gz)  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://fr.archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz](http://fr.archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz)  Could not connect to fr.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/source/Sources.gz)  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://fr.archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz](http://fr.archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz)  Could not connect to fr.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://fr.archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources.gz](http://fr.archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources.gz)  Could not connect to fr.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://fr.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz](http://fr.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz)  Could not connect to fr.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://fr.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz](http://fr.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz)  Could not connect to fr.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Failed to fetch [http://fr.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz](http://fr.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz)  Could not connect to fr.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://fr.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/source/Sources.gz](http://fr.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/source/Sources.gz)  Could not connect to fr.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by totfit on 2006-12-12
I am no expert at all, but it seems that for some reason you are not getting any connection at all. If you are behind a firewall disable it and try again. I sometimes have errors on some of the sources, but never all.

---

### Post by vaio pcgfxa53 dapper on 2006-12-13
firewall is bown, still having same problem, i can go online but cannot update.

---

### Post by Dusty545 on 2006-12-13
I could be barking up the wrong tree here but have you tried checking that your software sources are alright?

System -> Administration -> Software Sources

I'm using Edgy but there are two entries under the 'Authentication' tab and in your original post some of the output mentioned GPG.

I'm not the expert on this but someone might be able to suggest a way to rebuild the sources list.

Just a thought.

---

### Post by vaio pcgfxa53 dapper on 2006-12-13
i cant help but think that this sounds like a weird concequence of disabeling ipv6.  Prior to disabeling it in mozilla i was unable to go anywhere online.   Any thoughts or am i barking up the wrong tree?

---

### Post by Sef on 2006-12-13
> i cant help but think that this sounds like a weird concequence of disabeling ipv6. Prior to disabeling it in mozilla i was unable to go anywhere online. Any thoughts or am i barking up the wrong tree?

Try re-enabling it and see what happens.

---

### Post by rich.bradshaw on 2006-12-13
why did you disable it in the first place? Whats the point?

---

### Post by peterj on 2006-12-13
Depending on your system it can speed up browsing. I believe it can be disabled through mozilla or your computer. To check mozilla just key about:config in the address bar and search 'IPV6'

I could be barking up the wring tree but apt-update uses it's own setting for proxy's etc (as I had to change mine) maybe it is trying to go through a proxy?

---

### Post by konst88 on 2006-12-13
Do you have any other programs wich can go online except firefox? Like Gaim, Evolution, etc.

---

### Post by vaio pcgfxa53 dapper on 2006-12-13
because i had no net connection before i did.

---

### Post by vaio pcgfxa53 dapper on 2006-12-13
No evolution and Gaim dont work

---

### Post by konst88 on 2006-12-14
It is because of the ipv6 is not supported on your router.
Try using this guide:
[http://ubuntuforums.org/showthread.php?t=305275](http://ubuntuforums.org/showthread.php?t=305275)
Good luck.

---

### Post by vaio pcgfxa53 dapper on 2006-12-15
Thanks a bunch! I will give it a try and get back to everyone>

---

### Post by adamslade on 2006-12-19
I am also having the same problem where the DNS resolves archive.ubuntu.com or gb.archive.ubuntu.com to 1.0.0.0.  I knew it is a problem with the DNS lookup as I am unable to look it up on my other machines.  

I am running my own DNS server (on Win 2003) which refuses to resolve this, so I have checked out a number of other servers I can find (friends's, ISP's and other ISP's) and have not been able to get this resolved.  Having said that I did manage to resolve it yesterday off someone elses nameserver, but not been able to repeat it.  I have even tried querying the root nameservers.

-------
 EDIT
-------

I have now been able to solve this, after I found the entry in my DNS server cache and cleared it I was able to refresh and connect.

If anyone has problems getting this particular IP resolved they may find it useful to enter 82.211.81.173 as their DNS server.

Hope this helps someone!!

---

### Post by dbbd8 on 2006-12-30
I have the same problem. Did you resolve your problem? 
If yes, what was the solution.

Thanks,
Dan

---


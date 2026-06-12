---
title: "Problems With Update"
date: 2005-05-20
forum: Absolute Beginner Talk
---

### Post by animesh on 2005-05-20
hi
  whenever i try apt-get install i get the following error and it says run sudo apt-get update to remove these problems





W: Couldn't stat source package list [ftp://ftp.nerim.net](ftp://ftp.nerim.net) stable/main Packages (/var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_stable_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp.nerim.net](ftp://ftp.nerim.net) unstable/main Packages (/var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_unstable_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp.nerim.net](ftp://ftp.nerim.net) testing/main Packages (/var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_testing_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp.nerim.net](ftp://ftp.nerim.net) stable/main Packages (/var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_stable_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp.nerim.net](ftp://ftp.nerim.net) unstable/main Packages (/var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_unstable_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp.nerim.net](ftp://ftp.nerim.net) testing/main Packages (/var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_testing_main_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems



but when i do that get this



Err [ftp://ftp.nerim.net](ftp://ftp.nerim.net) stable/main Packages
  Could not connect to netmon.iitb.ac.in:21 (10.200.13.50), connection timed outErr [ftp://ftp.nerim.net](ftp://ftp.nerim.net) stable/main Release
  Could not connect to netmon.iitb.ac.in:21 (10.200.13.50), connection timed outErr [ftp://ftp.nerim.net](ftp://ftp.nerim.net) unstable/main Packages
  Could not connect to netmon.iitb.ac.in:21 (10.200.13.50), connection timed outErr [ftp://ftp.nerim.net](ftp://ftp.nerim.net) unstable/main Release
  Could not connect to netmon.iitb.ac.in:21 (10.200.13.50), connection timed outErr [ftp://ftp.nerim.net](ftp://ftp.nerim.net) testing/main Packages
  Could not connect to netmon.iitb.ac.in:21 (10.200.13.50), connection timed outErr [ftp://ftp.nerim.net](ftp://ftp.nerim.net) testing/main Release
  Could not connect to netmon.iitb.ac.in:21 (10.200.13.50), connection timed outFetched 69.8kB in 11m59s (97B/s)
Failed to fetch [ftp://ftp.nerim.net/debian-marillat/dists/stable/main/binary-i386/Packages.gz](ftp://ftp.nerim.net/debian-marillat/dists/stable/main/binary-i386/Packages.gz)  Could not connect to netmon.iitb.ac.in:21 (10.200.13.50), connection timed out
Failed to fetch [ftp://ftp.nerim.net/debian-marillat/dists/stable/main/binary-i386/Release](ftp://ftp.nerim.net/debian-marillat/dists/stable/main/binary-i386/Release)  Could not connect to netmon.iitb.ac.in:21 (10.200.13.50), connection timed out
Failed to fetch [ftp://ftp.nerim.net/debian-marillat/dists/unstable/main/binary-i386/Packages.gz](ftp://ftp.nerim.net/debian-marillat/dists/unstable/main/binary-i386/Packages.gz)  Could not connect to netmon.iitb.ac.in:21 (10.200.13.50), connection timed out
Failed to fetch [ftp://ftp.nerim.net/debian-marillat/dists/unstable/main/binary-i386/Release](ftp://ftp.nerim.net/debian-marillat/dists/unstable/main/binary-i386/Release)  Could not connect to netmon.iitb.ac.in:21 (10.200.13.50), connection timed out
Failed to fetch [ftp://ftp.nerim.net/debian-marillat/dists/testing/main/binary-i386/Packages.gz](ftp://ftp.nerim.net/debian-marillat/dists/testing/main/binary-i386/Packages.gz)  Could not connect to netmon.iitb.ac.in:21 (10.200.13.50), connection timed out
Failed to fetch [ftp://ftp.nerim.net/debian-marillat/dists/testing/main/binary-i386/Release](ftp://ftp.nerim.net/debian-marillat/dists/testing/main/binary-i386/Release)  Could not connect to netmon.iitb.ac.in:21 (10.200.13.50), connection timed out
Reading Package Lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

so cannot properly install or update plzzz provide a solution

---

### Post by mohaham on 2005-05-21
the   /etc/apt/sources.list  file may need to be updated..

here's the link for the How-to...
[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

---

### Post by animesh on 2005-05-21
thnks for the reply but i have already done that but still facing the problem

---

### Post by poofyhairguy on 2005-05-21
[QUOTE=animesh]thnks for the reply but i have already done that but still facing the problem[/QUOTE]


My tip:

don't use those M-what ever sources (I have trouble with french) Use the ubuntu backports instead (on forum). Has everything you need.

---

### Post by animesh on 2005-05-22
can u plz tell me from where can i get these ubuntu backport links and how to use them ?
may be i will have to edit the sources list and remove the FTP links...

---

### Post by MuddyWaters on 2005-06-22
Animesh,

I was getting the same problem. Folloing worked for me.
1. Go into Synaptic Pacage Manager.
2. Click on Setings / Repositories.
3. Disable the repository called ftp.nerim.net/....

The error went away. 

-Muddy

---


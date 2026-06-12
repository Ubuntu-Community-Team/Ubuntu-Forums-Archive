---
title: "Need help"
date: 2005-12-14
forum: Absolute Beginner Talk
---

### Post by Singachea on 2005-12-14
Hi buddies,

I got some problems with the repositories package addresses. I can't install anything because it says something like this:
[COLOR="Red"]
Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.[/COLOR]


[COLOR="Green"]http://archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg: Could not connect to archive.ubuntu.com:80 (82.211.81.182). - connect (111 Connection refused) [IP: 82.211.81.182 80]
[http://archive.ubuntu.com/ubuntu/dists/breezy-updates/Release.gpg:](http://archive.ubuntu.com/ubuntu/dists/breezy-updates/Release.gpg:) Could not connect to archive.ubuntu.com:80 (82.211.81.182). - connect (111 Connection refused) [IP: 82.211.81.182 80]
[http://archive.ubuntu.com/ubuntu/dists/breezy/restricted/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/breezy/restricted/source/Sources.gz:) Could not connect to archive.ubuntu.com:80 (82.211.81.182). - connect (111 Connection refused) [IP: 82.211.81.182 80]
[http://archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz:) Could not connect to archive.ubuntu.com:80 (82.211.81.182). - connect (111 Connection refused) [IP: 82.211.81.182 80]
[http://archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/binary-i386/Packages.gz:) Could not connect to archive.ubuntu.com:80 (82.211.81.182). - connect (111 Connection refused) [IP: 82.211.81.182 80]
[http://archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/binary-i386/Packages.gz:) Could not connect to archive.ubuntu.com:80 (82.211.81.182). - connect (111 Connection refused) [IP: 82.211.81.182 80][/COLOR]


I did try to update some of the repositories with many different guides, but i still got the same problems.

My internet seems to be ok, but i don't know what was wrong with this. I really have no idea to deal with this. Can anyone help out?

---

### Post by adwait on 2005-12-14
Try changing the archives to some other archives like say "us.archive.ubuntu.com" in yourr /etc/apt/sources.list file. Then run
```
sudo apt-get update
```

To edit the file:
```
sudo gedit /etc/apt/sources.list
```

---

### Post by ubuntu_demon on 2005-12-14
$sudo apt-get update

if that doesn't help you can change to the sources.list displayed here :
[https://wiki.ubuntu.com/BreezyUpgrade](https://wiki.ubuntu.com/BreezyUpgrade) OR you can use my sources.list (see my sig)

To edit your sources.list :
$sudo gedit /etc/apt/sources.list

To put the new sources.list to use :
$sudo apt-get update

I hope this solves your problem. Good luck!

---

### Post by Singachea on 2005-12-14
I followed the above steps and i still got some problems like this:


[COLOR="Red"]Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy Release.gpg
  Could not connect to us.archive.ubuntu.com:80 (216.165.129.138). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Packages
  Could not connect to us.archive.ubuntu.com:80 (216.165.129.138). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/multiverse Packages
  Could not connect to us.archive.ubuntu.com:80 (216.165.129.138). - connect (111 Connection refused)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/binary-i386/Packages.gz)  Could not connect to security.ubuntu.com:80 (82.211.81.138). - connect (111 Connection refused)
(/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
(/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/multiverse Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.[/COLOR]


What should I do?

---

### Post by ubuntu_demon on 2005-12-14
first replace your sources.list with the one here : [https://wiki.ubuntu.com/BreezyUpgrade](https://wiki.ubuntu.com/BreezyUpgrade)

That one should work unless there is a problem with the servers. 
try again :

$sudo apt-get update 

If you still have errors try pinging the servers and post the results here. For example :
$ping 123.123.123.123

If you want additional repo's add the ones from my recommended sources.list and repeat the process described above.

---


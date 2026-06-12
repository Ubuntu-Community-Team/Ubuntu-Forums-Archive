---
title: "apt-get update -&gt; Error :\"
date: 2006-07-24
forum: Absolute Beginner Talk
---

### Post by titaniumz on 2006-07-24
When I try to update with command: sudo apt-get update
I get this errors:

Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release.gpg
  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages
  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg)  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz)  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
Reading package lists... Done
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

what can I do?
also there are problems with the "repositories" (I dont even know what that is..) so when I open the "add application" window it says I have errors in the system.. :\

any help will be much appraised ;)

---

### Post by GuitarHero on 2006-07-24
Do you have an internet connection?  That error just means it cant access the repositories, which are where the files for programs you can install are held.  If you do have an internet connection, try again later, the server might have been breifly down.

---

### Post by s_h_a_d_o_w_s on 2006-07-24
It seems you don't have an active internet connection. 
If you are posting this on another pc, and cannot acces the internet, plug-in your modem so your pc can receive the internet. If you have ubuntu dapper drake, the ubuntu should connect automatically. If not, run

```
sudo pppoeconf 
```

in your terminal.
If that's not it, did you run 

```
apt-get update
```

? For help with the repositories, open synaptic ( system -> Administration -> synaptic package manager. Choose settings -> Repositories. Check each checkbox, then save and exit. that will enable all of the repositories. 

repositories are basically sources. say you want to install a program that is in a repository that hasn't been enabled in synaptic. (like we just did). then it won't be available to install, until you do. i hope that helped :-)

---

### Post by titaniumz on 2006-07-24
I do have an internet connection, I'm writing from that PC.
I have marked all of the repositories and now the errors number got bigger, it cant connect to any of them :\

Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.
[http://us.archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg:](http://us.archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg:) Could not connect to us.archive.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
[http://us.archive.ubuntu.com/ubuntu/dists/breezy-updates/Release.gpg:](http://us.archive.ubuntu.com/ubuntu/dists/breezy-updates/Release.gpg:) Could not connect to us.archive.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
[http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/Release.gpg:](http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/Release.gpg:) Could not connect to us.archive.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
[http://security.ubuntu.com/ubuntu/dists/breezy-security/Release.gpg:](http://security.ubuntu.com/ubuntu/dists/breezy-security/Release.gpg:) Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
[http://archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg:](http://archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg:) Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
[http://security.ubuntu.com/ubuntu/dists/breezy-security/main/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/breezy-security/main/binary-i386/Packages.gz:) Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
[http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/binary-i386/Packages.gz:) Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
[http://security.ubuntu.com/ubuntu/dists/breezy-security/main/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/breezy-security/main/source/Sources.gz:) Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
[http://us.archive.ubuntu.com/ubuntu/dists/breezy/main/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/breezy/main/binary-i386/Packages.gz:) Could not connect to us.archive.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
[http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/source/Sources.gz:) Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
[http://us.archive.ubuntu.com/ubuntu/dists/breezy/restricted/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/breezy/restricted/binary-i386/Packages.gz:) Could not connect to us.archive.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
[http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/binary-i386/Packages.gz:) Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
[http://us.archive.ubuntu.com/ubuntu/dists/breezy/main/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/breezy/main/source/Sources.gz:) Could not connect to us.archive.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
[http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/source/Sources.gz:) Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
[http://us.archive.ubuntu.com/ubuntu/dists/breezy/restricted/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/breezy/restricted/source/Sources.gz:) Could not connect to us.archive.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
[http://archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz:) Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
[http://us.archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz:) Could not connect to us.archive.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
[http://us.archive.ubuntu.com/ubuntu/dists/breezy/universe/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/breezy/universe/source/Sources.gz:) Could not connect to us.archive.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
[http://us.archive.ubuntu.com/ubuntu/dists/breezy-updates/main/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/breezy-updates/main/binary-i386/Packages.gz:) Could not connect to us.archive.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
[http://us.archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/binary-i386/Packages.gz:) Could not connect to us.archive.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
[http://us.archive.ubuntu.com/ubuntu/dists/breezy-updates/main/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/breezy-updates/main/source/Sources.gz:) Could not connect to us.archive.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
[http://us.archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/source/Sources.gz:) Could not connect to us.archive.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
[http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/main/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/main/binary-i386/Packages.gz:) Could not connect to us.archive.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
[http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/restricted/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/restricted/binary-i386/Packages.gz:) Could not connect to us.archive.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
[http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/binary-i386/Packages.gz:) Could not connect to us.archive.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
[http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/binary-i386/Packages.gz:) Could not connect to us.archive.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
[http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/main/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/main/source/Sources.gz:) Could not connect to us.archive.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
[http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/restricted/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/restricted/source/Sources.gz:) Could not connect to us.archive.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
[http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/source/Sources.gz:) Could not connect to us.archive.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
[http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/source/Sources.gz:) Could not connect to us.archive.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)

:confused:

---

### Post by titaniumz on 2006-08-23
I have reinstall entire ubuntu just to fix this problem and I have it again in the new version :( 
Its seems that something is ****** up with the DNS thingy, also as last time I couldnt see webpages with firefox until Iv'e changed: network.dns.disableIPv6 on firefox config to true(I dont know what that mean I just know that only like that I can see webpages!) 
also I cant add applications from the internet, and gaim wont connect with "login.icq.com" I have to ping it with terminal, see the IP and then insert the IP in the "Auth host"... this are all examples the problem I think is something with DNS and it concern all ubuntu system:\

---

### Post by ellism on 2006-10-03
I was also getting this error, so i have just pinged one of the servers on the list to see if it was a DNS problem and it could find it. so I tried again and now it works :-?.

---

### Post by ellism on 2006-10-04
further to this, after leaving it a while apt-get stops working, but if i ping the servers apt-get update works. But i can still not install aplications.  Its not just apt this seems be affecting though, can not connect to msn through Gaim.

---

### Post by tatimmer on 2006-10-04
"W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_bi nary-i386_Packages) - stat (2 No such file or directory)"

I have gotten this error because all your files in /var/lib/apt/lists/ are missing/deleted.

run "apt-get update" to restore the files and then back them up for the next time it happens.

---


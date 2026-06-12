---
title: "problems with source.list"
date: 2006-02-07
forum: Absolute Beginner Talk
---

### Post by bountonw on 2006-02-07
I tried to sudo apt-get update, but ran into problems. 

> ton@wmien01:~$ sudo apt-get update
Err [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) breezy Release.gpg
  Could not connect to th.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) breezy-updates Release.gpg
  Could not connect to th.archive.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
Err [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) breezy-backports Release.gpg
  Could not connect to th.archive.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
Ign [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) breezy-updates Release
33% [Connecting to th.archive.ubuntu.com (1.0.0.0)]q

I pressed Ctrl C to stop the opperation and re-group.

Then I copied the suggested source.list (after backing the old one up) from  Kyral's very useful tutorial thread 
[http://www.ubuntuforums.org/showthread.php?t=73885](http://www.ubuntuforums.org/showthread.php?t=73885)
post#33 

I ran sudo apt-get update again and got the following. 

> ton@wmien01:~$ sudo gedit /etc/apt/sources.list
ton@wmien01:~$ sudo apt-get update
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release.gpg
  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release.gpg
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release.gpg
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Sources
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages
  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages
  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Sources
  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Sources
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages
  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Sources
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg)  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy-updates/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/breezy-updates/Release.gpg)  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy-backports/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/breezy-backports/Release.gpg)  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/breezy-security/Release.gpg)  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed outFailed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy/main/binary-i386/Packages.gz)  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy/restricted/binary-i386/Packages.gz)  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/breezy/main/source/Sources.gz)  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/breezy/restricted/source/Sources.gz)  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz)  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/breezy/universe/source/Sources.gz)  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
ton@wmien01:~$


What should I do.  I want to install some soft ware, but don't want to proceed until I have this problem ironed out.

---

### Post by goatflyer on 2006-02-07
For some reason, your dns is resolving archive.ubuntu.com as 1.0.0.0 instead of its current address  82.211.81.182   Is your internet connection set up properly?

Are you using dialup or DSL?

Can you visit the ubuntu site [http://archive.ubuntu.com/](http://archive.ubuntu.com/) using firefox?  

What is the output from these commands? (you can see how the names resolve)

nslookup ubuntu.com
nslookup archive.ubuntu.com
nslookup [www.ubuntuforums.org](www.ubuntuforums.org)

---

### Post by bountonw on 2006-02-07
I am connected to DSL.  Got firefox working by disabling IPv6 according to 

post #4
[http://www.ubuntuforums.org/showthread.php?t=78337](http://www.ubuntuforums.org/showthread.php?t=78337)

But I still don't have any other internet access with gaim  (haven't tried any other programs.  So is that my problem?)

I originally saw the following thread that deals with this, but hadn't gotten around to doing anything as I didn't need anything but firefox at the time.
[http://www.ubuntuforums.org/showthread.php?t=125185](http://www.ubuntuforums.org/showthread.php?t=125185)

I followed your link via firefox and got 
> Index of /

    * ubuntu/

Apache/2.1.3 (Ubuntu) Server at archive.ubuntu.com Port 80

clicking on * ubuntu gave me

> Index of /ubuntu

    * Parent Directory
    * dists/
    * indices/
    * ls-lR.gz
    * pool/
    * project/

Apache/2.1.3 (Ubuntu) Server at archive.ubuntu.com Port 80


[QUOTE=goatflyer]What is the output from these commands? (you can see how the names resolve)

nslookup ubuntu.com
nslookup archive.ubuntu.com
nslookup [www.ubuntuforums.org](www.ubuntuforums.org)[/QUOTE]

I don't understand.

---

### Post by goatflyer on 2006-02-07
Okay, I can see you have partial connectivity.  You ARE hitting the correct ubuntu archives with firefox.

Open a terminal window  Applications>Accessories>Terminal

Type (or paste) the 3 commands I mentioned previously one at a time and copy the results back into a reply.

Afterwards you can type exit to quit terminal, or else click the x.  We want to see how those names get resolved.

---

### Post by bountonw on 2006-02-08
Finally came back from work and have the kids off to bed.  This is what I get from running the three commands.

> [COLOR="Red"]nslookup ubuntu.com[/COLOR][QUOTE]ton@wmien01:~$ nslookup ubuntu.com
Server:         192.168.1.1
Address:        192.168.1.1#53

Non-authoritative answer:
Name:   ubuntu.com
Address: 82.211.81.166

ton@wmien01:~$[/QUOTE]

> [COLOR="Red"]nslookup archive.ubuntu.com[/COLOR][QUOTE]ton@wmien01:~$ nslookup archive.ubuntu.com
Server:         192.168.1.1
Address:        192.168.1.1#53

Non-authoritative answer:
Name:   archive.ubuntu.com
Address: 82.211.81.182
[/QUOTE]

> [COLOR="Red"]nslookup [www.ubuntuforums.org[/COLOR]](www.ubuntuforums.org[/COLOR])[QUOTE]ton@wmien01:~$ nslookup [www.ubuntuforums.org](www.ubuntuforums.org)
Server:         192.168.1.1
Address:        192.168.1.1#53

Non-authoritative answer:
Name:   [www.ubuntuforums.org](www.ubuntuforums.org)
Address: 64.21.33.9
[/QUOTE]

---

### Post by bountonw on 2006-02-08
I have a new error with Synaptic 

> W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/multiverse Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_multiverse_binary-i386_Packages) - stat (2 No such file or directory)


I think that it is the same problem with my connectivity.

---

### Post by bountonw on 2006-02-08
I solved my internet connection problem and have updated and upgraded successfully.  The following link was the ticket for me.  I read through the entire thread trying things until I found the answer in post #28.  Not sure what it all means, but glad that it worked.

[http://www.ubuntuforums.org/showpost.php?p=708201&postcount=28](http://www.ubuntuforums.org/showpost.php?p=708201&postcount=28)

---

### Post by bountonw on 2006-02-08
This problem has been resolved.  I tried to edit the heading in the original post and mark as [RESOLVED], but do not see that option.

---

### Post by bountonw on 2006-02-09
My problem has now become unresolved again for both my home and office computers.

Home:  On my home computer I get the following message when I use synaptic.

> : Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/multiverse Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_multiverse_binary-i386_Packages) - stat (2 No such file or directory)

Office:  For my office computer synaptic doesn't list any Thai font packages when I do apt-get update , apt-get upgrade.

Warning messages kind of unnerve me, so any help on this would be appreciated.  Also would like to have the latest and greatest Thai updates so would like my sources.list to be correct for that.

---


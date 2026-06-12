---
title: "Help please package missing"
date: 2005-10-07
forum: Absolute Beginner Talk
---

### Post by bmarilena on 2005-10-07
Hi,
Trying again to install wine I followed the stepts in 

And after 
# apt-get build-dep wine

I got this answer:

[I]Reading package lists... Done
Building dependency tree... Done
E: Build-Depends dependency for wine cannot be satisfied because the package libicu28-dev cannot be found
[/I]

What can I do?
Anybody know where this package can be found, where adn how I should insert/install this in my ubuntu OS?

Marilena

---

### Post by pammiwhammi on 2005-10-07
I just looked in Synaptic. (Got to the foot, then System, then Administration, then Synaptic Package Manager.) It is listed in the Universe repository, but not the Ubuntu repository. Did you add the Universe repository in /etc/apt/sources.list? 

That may be the problem. If so, open a root terminal and type this; 

*sudo gedit /etc/apt/sources.list*

This file will open; 

deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
[U]deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted[/U]

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
[U] deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
 deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe[/U]

If you remove any pound signs from in front of the sources I have underlined that adds those repositories, and after doing apt-get update you should be able to install libicu28 in the normal way.

---

### Post by bmarilena on 2005-10-07
ok, I tryed and this is what I got :

[I]Failed to fetch [http://ro.security.ubuntu.com/ubuntu/dists/hoary/Release.gpg](http://ro.security.ubuntu.com/ubuntu/dists/hoary/Release.gpg)  Could not resolve 'ro.security.ubuntu.com'
Failed to fetch cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/dists/hoary/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/dists/hoary/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch [http://ro.security.ubuntu.com/ubuntu/dists/hoary/universe/binary-i386/Packages.gz](http://ro.security.ubuntu.com/ubuntu/dists/hoary/universe/binary-i386/Packages.gz)  Could not resolve 'ro.security.ubuntu.com'
Failed to fetch [http://ro.security.ubuntu.com/ubuntu/dists/hoary/universe/source/Sources.gz](http://ro.security.ubuntu.com/ubuntu/dists/hoary/universe/source/Sources.gz)  Could not resolve 'ro.security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hoary-security/Release](http://security.ubuntu.com/ubuntu/dists/hoary-security/Release) Unable to find expected entry  retricted/binary-i386/Packages in Meta-index file (malformed Release file?)
Reading package lists... Done
W: Couldn't stat source package list cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407) hoary/main Packages (/var/lib/apt/lists/Ubuntu%205.04%20%5fHoary%20Hedgehog%5f%20-%20Release%20i386%20(20050407)_dists_hoary_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407) hoary/restricted Packages (/var/lib/apt/lists/Ubuntu%205.04%20%5fHoary%20Hedgehog%5f%20-%20Release%20i386%20(20050407)_dists_hoary_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ro.security.ubuntu.com](http://ro.security.ubuntu.com) hoary/universe Packages (/var/lib/apt/lists/ro.security.ubuntu.com_ubuntu_dists_hoary_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/retricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security_retricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.
[/I] 
 and this for several times. 

and after # apt-get update 
 I got 
[I]Reading package lists... Done
Building dependency tree... Done
W: Couldn't stat source package list cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407) hoary/main Packages (/var/lib/apt/lists/Ubuntu%205.04%20%5fHoary%20Hedgehog%5f%20-%20Release%20i386%20(20050407)_dists_hoary_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407) hoary/restricted Packages (/var/lib/apt/lists/Ubuntu%205.04%20%5fHoary%20Hedgehog%5f%20-%20Release%20i386%20(20050407)_dists_hoary_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ro.security.ubuntu.com](http://ro.security.ubuntu.com) hoary/universe Packages (/var/lib/apt/lists/ro.security.ubuntu.com_ubuntu_dists_hoary_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/retricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security_retricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Could not open file /var/lib/apt/lists/ro.security.ubuntu.com_ubuntu_dists_hoary_universe_source_Sources - open (2 No such file or directory)
[/I]

I don't know what else I have to do.

Thanks

Marilena

---


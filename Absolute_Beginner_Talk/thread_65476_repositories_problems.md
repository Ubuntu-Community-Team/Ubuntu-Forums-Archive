---
title: "repositories problems?"
date: 2005-09-14
forum: Absolute Beginner Talk
---

### Post by bodhidharma on 2005-09-14
I'm getting errors on Synaptic start-up, as in:

s.org/backports/dists/hoary-extras/multiverse/binary-i386/Packages.gz: 401 Authorization Required
[http://backports.ubuntuforums.org/backports/dists/hoary-extras/restricted/binary-i386/Packages.gz:](http://backports.ubuntuforums.org/backports/dists/hoary-extras/restricted/binary-i386/Packages.gz:) 401 Authorization Required
[ftp://ftp.nerim.net/debian-marillat/dists/testing/sid/binary-i386/Packages.gz:](ftp://ftp.nerim.net/debian-marillat/dists/testing/sid/binary-i386/Packages.gz:) Unable to fetch file, server said 'Can't open /debian-marillat/dists/testing/sid/binary-i386/Packages.gz: No such file or directory  ' [IP: 62.4.17.14 21]
[ftp://ftp.nerim.net/debian-marillat/dists/testing/main/binary-i386/Packages.gz:](ftp://ftp.nerim.net/debian-marillat/dists/testing/main/binary-i386/Packages.gz:) Unable to fetch file, server said 'Can't open /debian-marillat/dists/testing/main/binary-i386/Packages.gz: No such file or directory  ' [IP: 62.4.17.14 21]
[ftp://ftp.nerim.net/debian-marillat/dists/testing/contrib/binary-i386/Packages.gz:](ftp://ftp.nerim.net/debian-marillat/dists/testing/contrib/binary-i386/Packages.gz:) Unable to fetch file, server said 'Can't open /debian-marillat/dists/testing/contrib/binary-i386/Packages.gz: No such file or directory  ' [IP: 62.4.17.14 21]
[ftp://ftp.nerim.net/debian-marillat/dists/testing/non-free/binary-i386/Packages.gz:](ftp://ftp.nerim.net/debian-marillat/dists/testing/non-free/binary-i386/Packages.gz:) Unable to fetch file, server said 'Can't open /debian-marillat/dists/testing/non-free/binary-i386/Packages.gz: No such file or directory  ' [IP: 62.4.17.14 21]


then


W: GPG error: [ftp://ftp.debian.org](ftp://ftp.debian.org) sid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F1D53D8C4F368D5D


then


W: Couldn't stat source package list [ftp://ftp.nerim.net](ftp://ftp.nerim.net) testing/maindeb Packages (/var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_testing_maindeb_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp.nerim.net](ftp://ftp.nerim.net) testing/ftp://ftp.debian.org/debian Packages (/var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_testing_ftp:__ftp.debian.org_debian_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp.nerim.net](ftp://ftp.nerim.net) testing/sid Packages (/var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_testing_sid_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp.nerim.net](ftp://ftp.nerim.net) testing/contrib Packages (/var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_testing_contrib_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp.nerim.net](ftp://ftp.nerim.net) testing/non-free Packages (/var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_testing_non-free_binary-i386_Packages) - stat (2 No such file or directory)



Any ideas as to why?  Similarly, I just got that little "updates available" icon,
and it says it has 102 updates, lots of libthis and libthat -- how do I know if
these are legit?


Thanks!

---

### Post by Leif on 2005-09-14
err, you shouldn't be using marillat or debian repositories. check ubuntuguide.org for the correct source list. (unless, of course, this is intentional)

---

### Post by XDevHald on 2005-09-14
Please understand that I am not bashing any users at all when I say this. 

"Do not reply to a thread without giving the user correct information if a user has incorrect information on their system and is using other information in which should not be there. Give them the correct information step by step as they're probably not skillfull or knowledgable in the area(s) that you're in."

First, open a terminal located in "Applications > System Tools > Terminal
> sudo gedit /etc/apt/sources.list

If you're using hoary, please replace everything that says breezy to hoary.

Then paste the below in your sources.list & save!

Then sudo apt-get update in terminal & then sudo apt-get upgrade

 > ## Uncomment the following two lines to fetch updated software from the network
deb [http://us.archive.ubuntu.com/ubuntu]("http://us.archive.ubuntu.com/ubuntu") breezy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu]("http://us.archive.ubuntu.com/ubuntu") breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu]("http://us.archive.ubuntu.com/ubuntu") breezy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu]("http://us.archive.ubuntu.com/ubuntu") breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu]("http://us.archive.ubuntu.com/ubuntu") breezy universe
deb-src [http://us.archive.ubuntu.com/ubuntu]("http://us.archive.ubuntu.com/ubuntu") breezy universe

deb [http://security.ubuntu.com/ubuntu]("http://security.ubuntu.com/ubuntu") breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu]("http://security.ubuntu.com/ubuntu") breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu]("http://security.ubuntu.com/ubuntu") breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu]("http://security.ubuntu.com/ubuntu") breezy-security universe

deb [http://archive.ubuntu.com/ubuntu]("http://archive.ubuntu.com/ubuntu") breezy multiverse
deb-src [http://archive.ubuntu.com/ubuntu]("http://archive.ubuntu.com/ubuntu") breezy multiverse


---

### Post by shrift on 2005-09-14
I believe the issue is that he wants something from those repositories, and he would like to retrieve those items via apt. He clearly had to have added those repositories himself as they dont come by default. So the issue is not how to change the sources.list, the issue is how to make the repositories work. 

I have the same issue with some of the repositories I want, Anyone know how to fix/disable whatever this public key issue?

---

### Post by aysiu on 2005-09-14
Use the repositories here, and they'll most likely fulfill your apt-getting needs:

[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

Be sure to completely replace what you have with what's in the guide. Don't just add on to what's already there.

---

### Post by shrift on 2005-09-14
Unfortunately it does not. What I want is the repositories for an application that has not made it into any kind of mainstream repositories. Its for a an audio application and the repository is maintained by the developer himself. When I add it and do an update I get the same "no public key" error as the person above. I have posted my own question on the forums here: [http://www.ubuntuforums.org/showthread.php?t=65621](http://www.ubuntuforums.org/showthread.php?t=65621)

---

### Post by aysiu on 2005-09-14
[QUOTE=shrift]Unfortunately it does not. What I want is the repositories for an application that has not made it into any kind of mainstream repositories. Its for a an audio application and the repository is maintained by the developer himself. When I add it and do an update I get the same "no public key" error as the person above. I have posted my own question on the forums here: [http://www.ubuntuforums.org/showthread.php?t=65621](http://www.ubuntuforums.org/showthread.php?t=65621)[/QUOTE]

If you mention the actual name of the application, that might help.

---

### Post by shrift on 2005-09-16
bodhidharma; the answer to this public key thing was discussed in this thread: [http://ubuntuforums.org/showthread.php?t=65621](http://ubuntuforums.org/showthread.php?t=65621) Check it out, I think you will find what you need.

---

### Post by poofyhairguy on 2005-09-16
[QUOTE=shrift]Unfortunately it does not. What I want is the repositories for an application that has not made it into any kind of mainstream repositories. Its for a an audio application and the repository is maintained by the developer himself. When I add it and do an update I get the same "no public key" error as the person above. I have posted my own question on the forums here: [http://www.ubuntuforums.org/showthread.php?t=65621](http://www.ubuntuforums.org/showthread.php?t=65621)[/QUOTE]

Just ignore the no public key thing. Basically that says "I'm installing from a place I don't trust, I hope you do."

---


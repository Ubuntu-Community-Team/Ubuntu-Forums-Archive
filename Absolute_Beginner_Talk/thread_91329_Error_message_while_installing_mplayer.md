---
title: "Error message while installing mplayer"
date: 2005-11-17
forum: Absolute Beginner Talk
---

### Post by endokrin on 2005-11-17
I went to Applications, Add Applications, and tried to select mplayer.
It said I need to go to Settings, Repositories to add the multiverse (whatever that is)
So I did and it said it was downloading new lists.
It appeared to finish downloading, then I get this pop-up Warning message:

> 
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/multiverse Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/multiverse Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)


What's wrong?

---

### Post by r0ll3r on 2005-11-17
Hi there,
on this thread [http://ubuntuforums.org/showthread.php?t=88153&page=3]("http://ubuntuforums.org/showthread.php?t=88153&page=3"), the same happened to someone. He was told, hit the reload button one more time. His problem was solved. Try it :)

---

### Post by endokrin on 2005-11-18
Hmmm.. I didn't see a reload button

I tried adding the multiverse again and got this message:

> 
Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

[http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/Release.gpg:](http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/Release.gpg:) Could not connect to antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
[http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/free/binary-i386/Packages.gz:](http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/free/binary-i386/Packages.gz:) Could not connect to antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
[http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/non-free/binary-i386/Packages.gz:](http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/non-free/binary-i386/Packages.gz:) Could not connect to antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
[http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/free/source/Sources.gz:](http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/free/source/Sources.gz:) Could not connect to antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
[http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/non-free/source/Sources.gz:](http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/non-free/source/Sources.gz:) Could not connect to antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)



I don't think it's my network since I'm online as I type..

Any ideas?

---


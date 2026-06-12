---
title: "Synaptic and upgrade problems"
date: 2007-08-12
forum: Absolute Beginner Talk
---

### Post by eaglescout1984 on 2007-08-12
I'm using Ubuntu 5.10 whcih for about  year has been running fine. Every few days I would recieve a notice to download and install the latest versions of my installed components. However, a few months back I noticed it stopped, but never paid it any attention.
Lately, I have been using Firefox 2.0 on my Windows boot and thought how nice it would be for Ubuntu's Firefox to be upraded. So, I went to Synaptic package manager and the latest verion listed was 1.5, I wondered if there was even a version 2.0 for Linux and looked on the Firefox website, sure enough there is.
After looking into it I realized there was a reload button on package manager, so I hit that. It begins the download. But before it gets half-way and says it can't find repository indicies and give me a large list.

```
http://security.ubuntu.com/ubuntu/dists/breezy-security/main/binary-i386/Packages.gz: 404 Not Found
http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/binary-i386/Packages.gz: 404 Not Found
http://security.ubuntu.com/ubuntu/dists/breezy-security/main/source/Sources.gz: 404 Not Found
http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/source/Sources.gz: 404 Not Found
http://archive.ubuntu.com/ubuntu/dists/breezy/main/binary-i386/Packages.gz: 404 Not Found [IP: 91.189.89.8 80]
http://archive.ubuntu.com/ubuntu/dists/breezy/restricted/binary-i386/Packages.gz: 404 Not Found [IP: 91.189.89.8 80]
http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/binary-i386/Packages.gz: 404 Not Found
http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/source/Sources.gz: 404 Not Found
http://archive.ubuntu.com/ubuntu/dists/breezy/main/source/Sources.gz: 404 Not Found [IP: 91.189.89.8 80]
http://archive.ubuntu.com/ubuntu/dists/breezy/restricted/source/Sources.gz: 404 Not Found [IP: 91.189.89.8 80]
http://archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz: 404 Not Found [IP: 91.189.89.8 80]
http://archive.ubuntu.com/ubuntu/dists/breezy/universe/source/Sources.gz: 404 Not Found [IP: 91.189.89.8 80]
http://archive.ubuntu.com/ubuntu/dists/breezy/multiverse/binary-i386/Packages.gz: 404 Not Found [IP: 91.189.89.8 80]
http://archive.ubuntu.com/ubuntu/dists/breezy/multiverse/source/Sources.gz: 404 Not Found [IP: 91.189.89.8 80]
http://archive.ubuntu.com/ubuntu/dists/breezy-updates/main/binary-i386/Packages.gz: 404 Not Found [IP: 91.189.89.8 80]
http://archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/binary-i386/Packages.gz: 404 Not Found [IP: 91.189.89.8 80]
http://archive.ubuntu.com/ubuntu/dists/breezy-updates/main/source/Sources.gz: 404 Not Found [IP: 91.189.89.8 80]
http://archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/source/Sources.gz: 404 Not Found [IP: 91.189.89.8 80]
http://archive.ubuntu.com/ubuntu/dists/breezy-backports/main/binary-i386/Packages.gz: 404 Not Found [IP: 91.189.89.8 80]
http://archive.ubuntu.com/ubuntu/dists/breezy-backports/restricted/binary-i386/Packages.gz: 404 Not Found [IP: 91.189.89.8 80]
http://archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/binary-i386/Packages.gz: 404 Not Found [IP: 91.189.89.8 80]
http://archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/binary-i386/Packages.gz: 404 Not Found [IP: 91.189.89.8 80]

```

Then it tells me the following problems were found with my system:

W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)

Any idea why I'm seeing these errors?

---

### Post by mikewhatever on 2007-08-12
[http://www.ubuntu.com/news/Ubuntu-5.10-end-of-life](http://www.ubuntu.com/news/Ubuntu-5.10-end-of-life)
5.10 is n longer supported, so the repositories are not there. You can either reinstall, in which case, any of the supported versions are ok (6.06,6.10,7.04), or upgrade to 6.06.

---


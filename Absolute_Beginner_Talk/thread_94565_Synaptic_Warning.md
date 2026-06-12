---
title: "Synaptic Warning"
date: 2005-11-24
forum: Absolute Beginner Talk
---

### Post by nierz on 2005-11-24
When I try to download something in the Synaptic Package Manager I get this error:

> W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/d/directfb/libdirectfb-0.9-22_0.9.22-0ubuntu3_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/d/directfb/libdirectfb-0.9-22_0.9.22-0ubuntu3_i386.deb)
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/multiverse/f/faad2/libfaad2-0_2.0.0+cvs20040908+mp4v2+bmp-0ubuntu2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/multiverse/f/faad2/libfaad2-0_2.0.0+cvs20040908+mp4v2+bmp-0ubuntu2_i386.deb)
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libg/libgii/libgii0-target-x_0.8.5-2ubuntu2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libg/libgii/libgii0-target-x_0.8.5-2ubuntu2_i386.deb)
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libg/libgii/libgii0_0.8.5-2ubuntu2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libg/libgii/libgii0_0.8.5-2ubuntu2_i386.deb)
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libg/libggi/libggi2_2.0.5-1ubuntu4_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libg/libggi/libggi2_2.0.5-1ubuntu4_i386.deb)
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/p/polypaudio/libpolyp0_0.7+20050805-2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/p/polypaudio/libpolyp0_0.7+20050805-2_i386.deb)
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/s/svgalib/libsvga1_1.4.3-22_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/s/svgalib/libsvga1_1.4.3-22_i386.deb)
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/multiverse/x/xvidcore/libxvidcore4_1.0.3-0.0_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/multiverse/x/xvidcore/libxvidcore4_1.0.3-0.0_i386.deb)
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/multiverse/m/mplayer/mplayer-386_1.0-pre7cvs20050716-0.1ubuntu9_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/multiverse/m/mplayer/mplayer-386_1.0-pre7cvs20050716-0.1ubuntu9_i386.deb)


How can I Fix this?

---

### Post by Pablo_Escobar on 2005-11-24
I'd recommend removing the "us" bit from /etc/apr/sources.list.

---

### Post by nierz on 2005-11-24
Meh...now when i try to open synaptic I get this:
Now its just giving me all kinda of errors.
Can someone give me a sources.list, because I think mine is messed.

> W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-updates_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/multiverse Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-updates_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/multiverse Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://seveas.ubuntulinux.nl](http://seveas.ubuntulinux.nl) breezy-seveas/all Packages (/var/lib/apt/lists/seveas.ubuntulinux.nl_dists_breezy-seveas_all_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/multiverse Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://cipherfunk.org](ftp://cipherfunk.org) breezy/main Packages (/var/lib/apt/lists/cipherfunk.org_pub_packages_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Packages (/var/lib/apt/lists/wine.sourceforge.net_apt_binary_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://people.ubuntu.com](http://people.ubuntu.com) ./ Packages (/var/lib/apt/lists/people.ubuntu.com_%7edoko_OOo2_._Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Packages (/var/lib/apt/lists/ftp.free.fr_pub_Distributions%5fLinux_plf_ubuntu_plf_dists_breezy_free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Packages (/var/lib/apt/lists/ftp.free.fr_pub_Distributions%5fLinux_plf_ubuntu_plf_dists_breezy_non-free_binary-i386_Packages) - stat (2 No such file or directory)

---

### Post by aysiu on 2005-11-24
See the first link in my sig.

---

### Post by nierz on 2005-11-24
Okay, that worked. Thanks.:p

---


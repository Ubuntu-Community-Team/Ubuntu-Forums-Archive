---
title: "Synaptic error (at load)"
date: 2006-02-18
forum: Absolute Beginner Talk
---

### Post by mednamot on 2006-02-18
W: Couldn't stat source package list [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Packages (/var/lib/apt/lists/ftp.free.fr_pub_Distributions%5fLinux_plf_ubuntu_plf_dists_breezy_free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Packages (/var/lib/apt/lists/ftp.free.fr_pub_Distributions%5fLinux_plf_ubuntu_plf_dists_breezy_non-free_binary-i386_Packages) - stat (2 No such file or directory)

my guess is that's coming from my sources.list...

my other guess is that was sources used by automatix, but I don't seem to always get the error, just from time to time...

heh, upon further review it seems I have 19 packages that can't currently be updated, one of which is Banshee, my guess is those 19 programs were received from the above sources yes?

think I should remove the lines from my sources.list, or should I just ignore the popup screen when I load up synaptic?

---

### Post by bfonseca on 2006-02-18
Hi I had the same problem just a few minutes ago.  your first guess would be the right one. Go into the /etc/apt and open up sources.list and just comment out the packages.([ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Packages (/var/lib/apt/lists/ftp.free.fr_pub_Distributions%5fLinux_plf_ubuntu_p) there should be two at the bottom. good luck

Brian

---


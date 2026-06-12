---
title: "apt-get update error"
date: 2006-01-15
forum: Absolute Beginner Talk
---

### Post by Griff on 2006-01-15
When running sudo apt-get update, I get an error at the bottom.  Funny thing is, it says I should run apt-get update to correct the problem.  :???:

Ign [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Packages
Get:8 [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Sources
Err [http://public.planetmirror.com](http://public.planetmirror.com) breezy/free Packages
  302 Found [IP: 203.16.234.20 80]
Err [http://public.planetmirror.com](http://public.planetmirror.com) breezy/non-free Packages
  302 Found [IP: 203.16.234.20 80]
Ign [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Sources
Get:9 [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Sources
Ign [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Sources
Hit [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Packages
Hit [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Packages
Hit [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Sources
Hit [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Sources
Fetched 3B in 5s (1B/s)
Failed to fetch [http://public.planetmirror.com/pub/plf/ubuntu/plf/dists/breezy/free/binary-i386/Packages.gz](http://public.planetmirror.com/pub/plf/ubuntu/plf/dists/breezy/free/binary-i386/Packages.gz)  302 Found [IP: 203.16.234.20 80]
Failed to fetch [http://public.planetmirror.com/pub/plf/ubuntu/plf/dists/breezy/non-free/binary-i386/Packages.gz](http://public.planetmirror.com/pub/plf/ubuntu/plf/dists/breezy/non-free/binary-i386/Packages.gz)  302 Found [IP: 203.16.234.20 80]
Reading package lists... Done
W: Couldn't stat source package list [http://public.planetmirror.com](http://public.planetmirror.com) breezy/free Packages (/var/lib/apt/lists/public.planetmirror.com_pub_plf_ubuntu_plf_dists_breezy_free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://public.planetmirror.com](http://public.planetmirror.com) breezy/non-free Packages (/var/lib/apt/lists/public.planetmirror.com_pub_plf_ubuntu_plf_dists_breezy_non-free_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by bullfrog on 2006-01-15
run in terminal   sudo apt-get update  that should fix it if not let us known    hope it works   bullfrog

---

### Post by Griff on 2006-01-15
No, it doesn't work.  Same errors keep coming up.  Ran it in the terminal 3 or 4 times with no change.

---

### Post by aysiu on 2006-01-15
[QUOTE=Griff]No, it doesn't work.  Same errors keep coming up.  Ran it in the terminal 3 or 4 times with no change.[/QUOTE] Get a different sources.list. See the first link of my sig.

---

### Post by Griff on 2006-01-15
Woo!  Fixed.  Updated with no errors.  Thanks!  :p

---


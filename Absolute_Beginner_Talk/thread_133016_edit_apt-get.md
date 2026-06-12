---
title: "edit apt-get"
date: 2006-02-19
forum: Absolute Beginner Talk
---

### Post by CookieOrc on 2006-02-19
where is the files to edit the apt-get list because it takes forever for me to do an update cause I get these errors 
```
Err ftp://ftp.free.fr breezy Release.gpg
  Read error - read (104 Connection reset by peer)
Ign ftp://ftp.free.fr breezy Release
Ign ftp://ftp.free.fr breezy/free Packages
Ign ftp://ftp.free.fr breezy/non-free Packages
Ign ftp://ftp.free.fr breezy/free Sources
Ign ftp://ftp.free.fr breezy/non-free Sources
Err ftp://ftp.free.fr breezy/free Packages
  Read error - read (104 Connection reset by peer)
Err ftp://ftp.free.fr breezy/non-free Packages
  Read error - read (104 Connection reset by peer)
Err ftp://ftp.free.fr breezy/free Sources
  Read error - read (104 Connection reset by peer)
Err ftp://ftp.free.fr breezy/non-free Sources
  Read error - read (104 Connection reset by peer)
Fetched 708B in 3m19s (4B/s)
Failed to fetch ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/breezy/Release.gpg  Read error - read (104 Connection reset by peer)
Failed to fetch ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/breezy/free/binary-i386/Packages.gz  Read error - read (104 Connection reset by peer)
Failed to fetch ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/breezy/non-free/binary-i386/Packages.gz  Read error - read (104 Connection reset by peer)
Failed to fetch ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/breezy/free/source/Sources.gz  Read error - read (104 Connection reset by peer)
Failed to fetch ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/breezy/non-free/source/Sources.gz  Read error - read (104 Connection reset by peer)
Reading package lists... Done
W: Couldn't stat source package list ftp://ftp.free.fr breezy/free Packages (/var/lib/apt/lists/ftp.free.fr_pub_Distributions%5fLinux_plf_ubuntu_plf_dists_breezy_free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list ftp://ftp.free.fr breezy/non-free Packages (/var/lib/apt/lists/ftp.free.fr_pub_Distributions%5fLinux_plf_ubuntu_plf_dists_breezy_non-free_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

```

I really do not know whats wrong but I figure if I removed them from the list it would be a whole lot easier to update

---

### Post by nalmeth on 2006-02-19
GNOME --> sudo gedit /etc/apt/sources.list
KDE --> sudo kwrite /etc/apt/sources.list

add a comment (##) to the lines you want to comment out, i.e. not use. That way you can reuse them later if you need to, and don't have to go looking for them again

The error messages do look untidy, but considering that you don't need to be updating all the time, it doesn't harm much

---

### Post by heimo on 2006-02-19
You can remove sources using Synaptic (these instructions are for adding, but you should get the idea):
[https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)

Or manually using text editor:
alt+F2+
```
gksudo gedit /etc/apt/sources.list
```

---


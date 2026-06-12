---
title: "Synaptic errors!"
date: 2005-12-29
forum: Absolute Beginner Talk
---

### Post by equal on 2005-12-29
Hey guys, I'm really stuck here. I installed Automatix, and ever since, when I open my Synaptic Package Manager, I get this error:

```

W: Couldn't stat source package list http://public.planetmirror.com breezy/free Packages (/var/lib/apt/lists/public.planetmirror.com_pub_plf_ubuntu_plf_dists_breezy_free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://public.planetmirror.com breezy/non-free Packages (/var/lib/apt/lists/public.planetmirror.com_pub_plf_ubuntu_plf_dists_breezy_non-free_binary-i386_Packages) - stat (2 No such file or directory)
```

As a result, I can't install ANYTHING. Every install I try gives me an error in the Terminal prompt that looks like this:

```

Err http://public.planetmirror.com breezy/non-free Packages
  Sub-process bzip2 returned an error code (2)
Fetched 171kB in 13s (12.7kB/s)
Failed to fetch http://public.planetmirror.com/pub/plf/ubuntu/plf/dists/breezy/free/binary-i386/Packages.gz  Sub-process bzip2 returned an error code (2)
Failed to fetch http://public.planetmirror.com/pub/plf/ubuntu/plf/dists/breezy/non-free/binary-i386/Packages.gz  Sub-process bzip2 returned an error code (2)
Reading package lists... Done
W: GPG error: http://public.planetmirror.com breezy Release: Unknown error executing gpgv
W: Couldn't stat source package list http://public.planetmirror.com breezy/free Packages (/var/lib/apt/lists/public.planetmirror.com_pub_plf_ubuntu_plf_dists_breezy_free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://public.planetmirror.com breezy/non-free Packages (/var/lib/apt/lists/public.planetmirror.com_pub_plf_ubuntu_plf_dists_breezy_non-free_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.
```

Any and all help is much appreciated!

---

### Post by r4ik on 2005-12-29
You could try "sudo apt-get install synaptic" in a terminal.
Good luck.
Duh would will give you its already there i suppose.
Try remove Automatix.
Try to re-install synaptic see if that works.

---

### Post by prizrak on 2005-12-30
Go to Synaptic>Settings>Repositories click on Settings and enable "Show disabled software sources" then uncheck all the repositories that are URLs ([http://something.something](http://something.something)) then click OK and it will prompt you to reload the database. That *should* help you.

---

### Post by arnieboy on 2005-12-30
these errors are because of the planetmirror repos being down. they have been removed in the latest ersion of automatix. please redownload and reinstall automatix. read the main automatix thread for more details.

---


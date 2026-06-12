---
title: "What are &quot;Installed (auto-removable)&quot; packages in Synaptics??"
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by kilou on 2007-05-01
Hi,

just wondering what are "Installed (auto-removable)" packages in Synaptics. Should I uninstall those packages or just leave them there? Why are they in this category?

A few days ago I only had "Docker" in the list of autoremovable packages but now I have:

Docker
libdvbpsi4
libiso9660-4
libpostprocd
libtar
libvcdinfo0
libxosd2

I think the list of lib* packages appeared after I removed VLC player (vlc appears to be dependant on those packages). However I checked the dependencies of those packages and it seems that all the packages that depends on the above names are not installed on my system.....so I assume it should be safe to remove them no? One exception: amsn depends on docker and amsn is installed on my system...

I don't understand why removing VLC didn't remove those packages as well since they are not required for any program installed on my system. I used **sudo aptitude remove vlc **to uninstall VLC...
Any help to clarify this would be appreciated! Thanks

---

### Post by Seisen on 2007-05-01
Autoremovable packages are  packages that were installed as a dependency for another package, and the original package has now been removed.

So it would be safe to remove them. If you have problems with amsn just reinstall it using apt-get or synaptic.

---

### Post by kilou on 2007-05-01
Thanks! This makes sense :) I've removed all the lib* packages but left Docker. Amsn has not been installed from a package but has been compiled from source to get the "antialiasing fix". This is probably why Synaptics thinks that Docker is no more required and put it in the auto removable category.

---


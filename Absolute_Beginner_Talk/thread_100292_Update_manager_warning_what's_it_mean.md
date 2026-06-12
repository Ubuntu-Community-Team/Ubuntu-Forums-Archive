---
title: "Update manager warning what's it mean?"
date: 2005-12-07
forum: Absolute Beginner Talk
---

### Post by jockjunior on 2005-12-07
hello again,
   need your help again got his message when starting update manager a few mins ago. Download stuff ok. but dont understand this :confused: 


W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/main Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20i386%20(20051012)_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/restricted Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20i386%20(20051012)_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)

any offers ? 
any explanation/help appreciated

thanks
Jock

---

### Post by Pablo_Escobar on 2005-12-07
do 
> sudo gedit /etc/apt/sources.list

put a hash (#) sign in front of the line which says "cdrom" - it should be the first line

---

### Post by jockjunior on 2005-12-07
Thank you my friend :smile: 
Once again you came to my rescue much obliged.
Could have something to do with me downloading EasyBreezy last night? 

jock

---

### Post by Pablo_Escobar on 2005-12-07
Humpf, I can't say because I don't use it.
This entry pointed to the installation Breezy CD-ROM, which if You've installed the system, and have net access is not needed :)

Glad to see it helped :)

---

### Post by jockjunior on 2005-12-07
Thanks again for quick reply (one day I'll get the hang of this )
cheers

jock

---

### Post by Gray. on 2005-12-07
The CD repo is the only one that is added at initial installation of Ubuntu. You just have to go
System > Administration > Synaptic Package Manager > Settings > Repositories
then untick the CD-Rom entry. Or edit the /etc/apt/sources.list Though newbies may be turned off by text editors and command-line. :)

---


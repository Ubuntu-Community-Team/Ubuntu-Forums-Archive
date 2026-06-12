---
title: "help installing"
date: 2006-04-30
forum: Absolute Beginner Talk
---

### Post by cptjaben on 2006-04-30
hi, i'm trying to install Gnomad for my [Creative Nomad Jukebox Zen Xtra]("http://www.nomadworld.com/products/Jukebox_ZenXtra/"), i'm following [this HOWTO: ]("http://ubuntuforums.org/showthread.php?t=33040&highlight=creative+nomad+zen") and i'm wondering if anyone knows how to install the development libraries from libusb. 

thanks.

---

### Post by AnRuaRi on 2006-04-30
the first thing I allways do is open the synaptic Package manager and search for what I'm looking for.
I would check right now if what you're looking for is there, but I'm running Automatix right now so I cant open any other package manager.

If you've not used it before Synaptic is on your System menu 

System -> Administration -> Synaptic Package Manager

Make sure you have your repositories installed. these can be installed from the menu's at the top of the screen.

---

### Post by Sef on 2006-04-30
To learn how to add repositories, click on the link.

[https://wiki.ubuntu.com/AddingRepositoriesHowto]("https://wiki.ubuntu.com/AddingRepositoriesHowto")

---

### Post by cptjaben on 2006-05-03
ok, so i found the package from the libusb library but i get this error message when i try to install it:

W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/main Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20i386%20(20051012)_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/restricted Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20i386%20(20051012)_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)


does anyone know how to fix this or how to install the development libraries for libusb.

Thanks

---

### Post by nanotube on 2006-05-03
[QUOTE=cptjaben]ok, so i found the package from the libusb library but i get this error message when i try to install it:

W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/main Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20i386%20(20051012)_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/restricted Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20i386%20(20051012)_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)


does anyone know how to fix this or how to install the development libraries for libusb.

Thanks[/QUOTE]
well, it seems like its trying to locate the package on your install cd. try shoving in the install cd, and click "reload" in synaptic, then try again

---

### Post by cptjaben on 2006-05-03
ahh ok, thanks.

---


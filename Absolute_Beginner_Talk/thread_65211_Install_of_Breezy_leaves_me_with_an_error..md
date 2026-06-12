---
title: "Install of Breezy leaves me with an error."
date: 2005-09-13
forum: Absolute Beginner Talk
---

### Post by nitricacid on 2005-09-13
Ok, i just updated to Breezy by doing a whole 'sudo apt-get dist-upgrade' cmd and then once that was done installing i ran 'sudo apt-get update' becuase it told me to at the end of the isntall and everything apears to be running smooth but i have a few bugs that noticed.

Here is what it says when I used the apt-get update

Sudo apt-get update
password:
Ign cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20050909) breezy Release.gpg
Ign cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20050909) breezy Release
Ign cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20050909) breezy/main Packages
Ign cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20050909) breezy/restricted Packages
Err cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20050909) breezy/main Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20050909) breezy/restricted Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy Release.gpg [189B]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release.gpg [189B]
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg [189B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources
Fetched 3B in 0s (4B/s)
Failed to fetch cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20050909)]/dists/breezy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20050909)]/dists/breezy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Reading package lists... Done
W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20050909) breezy/main Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20i386%20(20050909)_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20050909) breezy/restricted Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20i386%20(20050909)_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

I am not sure what files it needs since i really don't know how to read linux command to well but it looks like to be something with cdrom. 
Which is weird cuz my CD rom drive works fine on mounting and unmounting CD's

Also there are things that fail to load when I start/shutdown linux,
1. General Console Font (startup)
2. ror: temperary failure in name resolution (shutdown)
3. T_kernel_font invalid request (shutdown)

If someone could please help me in these matters it would be greatly apreciated.

Thanks

---

### Post by aysiu on 2005-09-13
Maybe you should try commenting the CD-ROM out of your sources.list, seeing as how you have all the Breezy internet repositories already.

Just *sudo gedit /etc/apt/sources.list* and put *##* in front of the CD-ROM line.
Then, *sudo apt-get update*.

---

### Post by drewbie on 2005-09-13
Hi 

i too have the general console font fail sign at startup but it doesn't seem to have any adverse effects for me it seems to just be a bug [http://www.ubuntuforums.org/showthread.php?t=43899](http://www.ubuntuforums.org/showthread.php?t=43899)

if like me you did the apt-get dist-upgrade then you will not have the CD, not that its needed, so just pust a hash at the begining of the cdrom line in /etc/apt/sources.list (its the first one i think)

as for the rest of the sources i'm not sure

---

### Post by nitricacid on 2005-09-13
Sweet, thanks  :)

---

